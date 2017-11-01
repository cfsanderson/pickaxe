# Notes on Programming Ruby by Dave Thomas

Below are my personal note for the Programming Ruby book by Dave Thomas.

_____
## 1.4
By using the "shebang" notation at the top of a file...
```
#!/usr/bin/ruby
puts "Hello, world"
```
and changing the mode of the file using `chmod +x <filename>` you can make a ruby file executable. Enter `ruby <./filename>` in the command line to execute.

## 1.5
- `ri --help`

I have set `export RI="--format ansi --width 70"` in .zshrc

## 2.1 Ruby Is and Object-Oriented Language
Jukebox analogy
Song = a class with several instances ("Ruby Tuesday", "Small Talk", etc.)
Object == class instance

constructor = special method associated w/ a class. Standard constructor is called `new`

song1 = Song.new("Ruby Tuesday")
song2 = Song.new("Enveloped in Python")

Different but have unique characteristics
- object identifier
- instance variables (vars with values that are unique to each instance).
  - instance vars hold an object's state (such as the title of the song).

Within each class can define _instance methods_. Instance methods are a chunk of functionality that can be called in the context of the class and (depending on accessibility constraints) from outside the class.
- ex. "play" instance method - call the method, play the song.

`puts "gin joint".length`
- puts = method
- "gin joint" = receiver
- ".length" = method to be invoked

2 method calls - puts and .length

Single vs. Double-quoted strings...

- single-quoted string - Ruby does less work
- double-quoted strings - Ruby looks for chars like "/n". or interpolates with the #{var} syntax.

Ruby names...
- local vars, method params, and method names = start with a lowercase letter or an underscore_
- global vars = prefixed with a "$"
- instance vars = begin with an @
  - chars following @ cannot be a number
- class vars = begin with two @@
- class names, module names, and constants = start with an uppercase letter.

Convention is that....
- multiword instance vars are wretten with underscores between words
- multiword class names are written in MixedCase (CamelCase)
- method names may end with the chars ?, !, and =.

Examples...
- Local Variable: `name fish_and_chips x_axis thx1138 _x _26`
- Instance Variable: `@name @point_1 @X @_ @plan9`
- Class Variable: `@@total @@symtab @@N @@x_pos @@SINGLE`
- Global Variable: `$debug $CUSTOMER $_ $plan9 $Global`
- Class Name: `String ActiveRecord MyClass`
- Constant Name: `FEET_PER_MILE DEBUG`


## 2.3 Arrays and Hashes
Both store cllections of objects, accessible using a key
- arrays use and integer as key (more efficient)
- hashes support any object as a key (more flexible)

`nil` is an object in Ruby that happens to represent nothing. Produces false in conditionals.

### Arrays...
`a = [ 'ant', 'bee', 'cat', 'dog', 'elk' ]`
or
`a = %w{ ant bee cat dog elk }`

a[0] #=> "ant"

### Hash map (keys and values)...
```
inst_section = {
  'cello' => 'string',
  'clarinet' => 'woodwind',
  'drum' => 'percussion',
  'oboe' => 'woodwind',
  'trumpet' => 'brass',
  'violin' => 'string'
}
```

## 2.4 Symbols
Symbols are constant names that you don't have to predeclare and are guaranteed to be unique
Syntax....
- `:variable_name` as in...
- `method(:variable_name)`

Symbols frequently used as keys in hashes.
```
inst_section = {
  :cello => 'string',
  :clarinet => 'woodwind',
  :drum => 'percussion',
  :oboe => 'woodwind',
  :trumpet => 'brass',
  :violin => 'string'
}
```
shortcut syntax leaves off the : in the above example b/c so common.

## 2.5 Control Structures
`if` statements and `while` loops are terminated with `end`

in...
```
while line = gets
  puts line.downcase
end
```
Assignment sets line to either next line or `nil`. Since this returns a value, `gets` interprets that there is a value present from `line` after the loop and if `nil` it will exit the loop.

## 2.6 Regular Expressions
Regex is built in to Ruby :)

## 2.7 Blocks and Iterators
_Code blocks_ are chunks of code you can associate with method invocations, almost as if they were parameters. Can be used to implement callbacks

`{}` for single-line blocks
`do-end` for multi-line blocks
