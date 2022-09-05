![text](crubystal.png)

crubystal allows you to write your [ruby](https://ruby-lang.org) extensions in [Crystal](https://crystal-lang.org).

With Crystal's very similar syntax and great performance you can swap just those parts which need it,
with less suffering while doing do so.

```crystal
# yourCodeFile.cr
require "./crubystal"
fun init="Init_nameOfYourAwesomeExtension"; end

addGlobalMethod "foo", 4 do |r, who, amount, what, pluralSuffix|  
 v "#{v who} ate #{v amount} #{v what}#{v pluralSuffix unless v(amount)==1}!"  
end
```

Build it with `crystal build yourCodeFile.cr -o nameOfYourAwesomeExtension.bundle`, load it into your ruby application and enjoy!

```ruby
require_relative 'nameOfYourAwesomeExtension'
puts foo "I", 5, "doughnut", "s" 
```

Thia project just started and it's still a work in progress - so far you can  
- [ ] define global variables  
- [ ] add methods  
- [x] add global methods  
- [ ] ~~define alias~~[^1]  
- [ ] ~~undefine methods~~[^1]    
- [ ] define constants  
- [ ] define global constants  
- [ ] add modules  
- [ ] ~~call ruby methods~~[^1]     
- [ ] raise    
- [ ] ~~access variables on your own~~[^1]    

[^1]:  uncertain if those are even worth/useful to implement;  
     if there is a good reason to implement those, they could get reconsidered  
    
and receive data of types  
- [x] Nil  
- [x] True  
- [x] False  
- [x] Symbols[^2]    
- [x] String up to a length of  
    - [x] 23 bytes  
    - [x] 18446744073709551616 bytes  
- [x] Integer (signed and unsigned) of up to 
    - [x] 63 bytes  
    - [x] unlimited  
- [x] Float (signed and unsigned) of up to 
    - [x] 62 bytes  
    - [x] unlimited      
- [x] Arrays  
- [x] Hashes  
[^2]: In order to create symbols in Crystal at runtime there is the somewhat hacky shard/module symbolx required. You should not create more than 2^31 symbols to stay on the safe side, although you likely will be safe for almost 2^32 symbols. Just keep that in mind. If you want to be 100% safe, stay in ruby, if you want to be safer than what I'm offering out of the box, don't send symbols to your crubystal extension. But there really should no need to worry for up to 2^31 symbols either. 
