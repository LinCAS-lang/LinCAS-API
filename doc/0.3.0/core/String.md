# Class: String
A string is a sequence of UTF-8 characters enclosed 
betweend double quotes.

Up to now no special characters have been introduced 
(like '\n' or similar) nor particular string options
like string interpolation, but they're planned to be implemented in future.

Users must be careful with method aliases: this type has methods
which modify the content of a sring, and others which return a new one.
The first ones usually end with `!`, but there are some exceptions
like `String#[]=`

## Defined in:
String.cr

---
## Index:
  * [#*](#str--integer--new_string)
  * [#+](#str--other_str--new_str)
  * [#==](#str--other--boolean)
  * [#[]](#strindex--string-or-null)
  * [#[]=](#strindex--string--str)
  * [#chars](#chars--array-)
  * [#clone](#clone--new_str)
  * [#compact](#compact--new_str)
  * [#compact!](#compact--str)
  * [#concat](#concatstr1str2str3--str)
  * [#each ](#each&block--str)
  * [#gsub](#gsubpatternreplacement--new_str)
  * [#hash](#hash--integer)
  * [#include?](#includestring--boolean)
  * [#init](#initstring--new_string)
  * [#insert](#insertindexstring--str)
  * [#lowcase](#lowcase--new_string)
  * [#lowcase!](#lowcase--str)
  * [#size](#size--integer)
  * [#split](#splitdelimiter--"-"--array)
  * [#starts_with?](#starts_withstr_beg--boolean)
  * [#to_f](#to_f--float)
  * [#to_i](#to_i--integer)
  * [#to_sym](#to_sym--symbol)
  * [#upcase](#upcase--new_string)
  * [#upcase!](#upcase--str)
---
### str * integer -> new_string

Performs a multiplication between a string and a number
```coffee
bark   := "Bark"
bark_3 := bark * 3 #=> "BarkBarkBark"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L368)

### str + other_str -> new_str


Adds two strings.
This method can be invoked in two ways:
```coffee
foo    := "Foo"
bar    := "Bar"
foobar := foo + bar #=> "FooBar"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L309)

### str == other -> boolean

Compares two strings or a string with another object
```coffee
bar := "Bar"
foo := "Foo"
bar == bar #=> true
bar == foo #=> false
bar == 2   #=> false
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L428)

### str[index] -> string or null
### str[range] -> string 

Access the string characters at the given index
```coffee
str := "A quite long string"
str[0]    #=> "A"
str[8]    #=> "l"
str[2..6] #=> "quite"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L510)

### str[index] = string -> str

Sets a char or a set of chars in a specified index
```coffee
a    := "Gun"
a[0] := "F"    #=> "Fun"
a[2] := "fair" #=> "Funfair"
a[8] := "!"    #=> Raises an error
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L584)

### chars() -> array 

Returns an array containing each char of the string
```coffee
"abc".chars() #=> ["a","b","c"]
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L849)

### clone() -> new_str

Clones a string
```coffee
a := "Foo"
b := a         # b and a are pointing to the same object
# Now b and c are going to point to two different objects
c := a.clone() #=> "Foo"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L469)

### compact() -> new_str

Clones the string and deletes the spaces on this last
one
```coffee
"Compacting This String".compact() #=> "CompactingThisString"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L872)

### compact!() -> str

Deletes the spaces of str
```coffee
"Compacting This String".compact!() #=> "CompactingThisString"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L902)

### concat(str1,str2,str3...) -> str

Concatenates other strings at the given one
```coffee
a := "1"
a.concat("2")     #=> "12"
a.concat("3","4") #=> "1234"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L338)

### each(&block) -> str

Iterates over each char of the string
```coffee
"abcd".each_char() { (chr)
print "Char: ",chr
printl
}

#=> Char: a
#=> Char: b
#=> Char: c
#=> Char: d
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L827)

### gsub(pattern,replacement) -> new_str

Returns a new string where every occurrence 
of `pattern` replaced with the content in `replacement`
```coffee
"comfort".gsub("o","*")    #=> c*mf*rt
"comfort".gsub("com","ef") #=> effort
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L969)

### hash() -> integer

Return string hash based on length and content

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L1070)

### include?(string) -> boolean

Checks if a substring is contained in another one.
It works making a call like this:
```coffee
str := "A cat on the roof"
cat := "Cat"
str.include(cat)   #=> true
str.include("bed") #=> false
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L400)

### init(string) -> new_string


Initializes a new string through the keyword 'new' or just
assigning it. This is the 'init' method of the class
```coffee
str := "Foo"             #=> Foo
str := new String("Foo") #=> Foo
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L277)

### insert(index,string) -> str

Inserts a second string in the current one
```coffee
a := "0234"
a.insert(1,"1") #=> "01234"
a.insert(5,"5") #=> "012345"
a.insert(7,"6") #=> Raises an error
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L548)

### lowcase() -> new_string

Performs the downcase on the whole string 
without overwriting the original one
```coffee
"FOO.lowcase() #=> "foo"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L703)

### lowcase!() -> str

Performs the downcase on the whole string overwriting the original one
```coffee
"FOO.lowcase!() #=> "foo"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L680)

### size() -> integer
### length() -> integer [alias]

Returns the string size
```coffee
a := "Hello, world"
a.size() #=> 12
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L619)

### split(delimiter := " ") -> array

Splits a string according to a specific delimiter, returning an array.
If `delimiter` is not specified, a white space will be used
```coffee
a := "a,b,c,d"
a.split(",") #=> ["a","b","c","d"]
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L730)

### starts_with?(str_beg) -> boolean

Returns true if the beginning of `str` matches `str_beg`, 
false in all the other cases
```coffee
"hola".starts_with? ("h")  #=> true
"hola".statrs_with? ("ho") #=> true
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L1006)

### to_f() -> float

Converts a string into a float number
```coffee
"12".to_f()     #=> 12.0
"12.24".to_f()  #=> 12.24
"12.ab".to_f()  #=> 12.0
"abcd".to_f()   #=> 0.0
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L803)

### to_i() -> integer

Converts a string into an integer number.
Warning: no overflow is checked yet
```coffee
"12".to_i()   #=> 12
"12x".to_i()  #=> 12
"abcd".to_i() #=> 0
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L784)

### to_sym() -> symbol

Converts `str` into a symbol
```coffee
"foo".to_sym() #=> :foo
"32".to_sym()  #=> :"32"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L1047)

### upcase() -> new_string

Performs the upcase on the whole string 
without overwriting the original one
```coffee
"foo".upcase() #=> "FOO"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L658)

### upcase!() -> str

Performs the upcase on the whole string overwriting the original one
```coffee
"foo".upcase!() #=> "FOO"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L635)

