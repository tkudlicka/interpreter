# Interpreter in go

Programming language interpreter designed in [_Writing An Interpreter In Go_](https://interpreterbook.com/).


## Usage
It's for educational purpose.

## Getting started

### Variable bindings and number types

You can define variables using `let` keyword. Supported number types are integers and floating-point numbers.

```sh
>> let a = 1;
>> a
1
>> let b = 0.5;
>> b
0.5
```

### Arithmetic expressions

You can do usual arithmetic operations against numbers, such as `+`, `-`, `*` and `/`.

```sh
>> let a = 10;
>> let b = a * 2;
>> (a + b) / 2 - 3;
12
>> let c = 2.5;
>> b + c
22.5
```


### Strings

You can build strings using a pair of double quotes `""`. Strings are immutable values just like numbers. You can concatenate strings with `+` operator.

```sh
>> let makeGreeter = fn(greeting) { fn(name) { greeting + " " + name + "!" } };
>> let hello = makeGreeter("Hello");
>> hello("John");
Hello John!
```

### Arrays

You can build arrays using square brackets `[]`. Arrays can contain any type of values, such as integers, strings, even arrays and functions (closures). To get an element at an index from an array, use `array[index]` syntax.

```sh
>> let myArray = ["Thorsten", "Ball", 28, fn(x) { x * x }];
>> myArray[0]
Thorsten
>> myArray[4 - 2]
28
>> myArray[3](2);
4
```

### Hash tables

You can build hash tables using curly brackets `{}`. Hash literals are `{key1: value1, key2: value2, ...}`. You can use numbers, strings and booleans as keys, and any type of objects as values. To get a value of a key from a hash table, use `hash[key]` syntax.

```sh
>> let myHash = {"name": "Jimmy", "age": 72, true: "yes, a boolean", 99: "correct, an integer"};
>> myHash["name"]
Jimmy
>> myHash["age"]
72
>> myHash[true]
yes, a boolean
>> myHash[99]
correct, an integer
```

### Built-in functions

There are many built-in functions in Monkey, for example `len()`, `first()` and `last()`. Special function, `quote`, returns an unevaluated code block (think it as an AST). Opposite function to `quote`, `unquote`, evaluates code inside `quote`.

```sh
>> len("hello");
5
>> len("∑");
3
>> let myArray = ["one", "two", "three"];
>> len(myArray)
3
>> first(myArray)
one
>> rest(myArray)
[two, three]
>> last(myArray)
three
>> push(myArray, "four")
[one, two, three, four]
>> puts("Hello World")
Hello World
nil
>> quote(2 + 2)
Quote((2 + 2)) # Unevaluated code
>> quote(unquote(1 + 2))
Quote(3)
```
