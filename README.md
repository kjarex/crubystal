Rubylizer allows you to write your ruby extensions in [Crystal](https://crystal-lang.org).

With Crystal's very similar syntax and great performance you can swap just those parts which need it,
with less suffering while doing do so.

```crystal
# yourCodeFile.cr
require "./rubylizer"
fun init="Init_nameOfYourAwesomeExtension"; end

addGlobalMethod "foo", 1 do |r, who, amount, pluralSuffix|  
 "#{who} ate #{amount} #{what}#{pluralSuffix unless amount==1}!"  
end
```

Build it with `crystal build yourCodeFile.cr -o nameOfYourAwesomeExtension.bundle`, load it into your ruby application and enjoy!

```ruby
require_relative 'nameOfYourAwesomeExtension'
puts foo "I", 5, "doughnut", "s" 
```

Thia project just started and it's still a work in progress - so far you can  
[ ] define global variables  
[ ] add methods  
[x] add global methods  
[-] define alias\*  
[-] undefine methods\*  
[ ] define constants  
[ ] define global constants  
[ ] add modules  
[-] call ruby methods\*   
[-] raise\*  
[-] access variables on your own\*  

\*:  uncertain if those are even worth/useful to implement;  
     if there is a good reason to implement those, they could get reconsidered  
    
and receive data of types  
[x] Nil  
[x] True  
[x] False  
[ ] Symbols  
[x] String up to a length of  
[x] 23 bytes  
    [x] 18446744073709551616 bytes  
[o] Integer (signed and unsigned)  
    [x] 63 bytes  
    [ ] unlimited  
[o] Float (signed and unsigned)  
    [x] 62 bytes  
    [ ] unlimited      
[ ] Arrays  
[ ] Hashes  
