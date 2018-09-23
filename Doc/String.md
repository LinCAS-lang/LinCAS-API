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
---
String.cr

---
##Index:
  * [#+()](#str--other_str---new_str)
  * [#concat()](#concatstr1str2str3---str)
  * [#init()](#initstring---new_string)
---
### str + other_str -> new_str


Adds two strings.
This method can be invoked in two ways:
```CoffeeScript
foo    := "Foo"
bar    := "Bar"
foobar := foo + bar #=> "FooBar"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L309)

### concat(str1,str2,str3...) -> str

Concatenates other strings at the given one
```
a := "1"
a.concat("2")     #=> "12"
a.concat("3","4") #=> "1234"
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L338)

### init(string) -> new_string


Initializes a new string through the keyword 'new' or just
assigning it. This is the 'init' method of the class
```CoffeeScript
str := "Foo"             #=> Foo
str := new String("Foo") #=> Foo
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/String.cr#L277)

