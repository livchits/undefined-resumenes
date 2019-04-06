#Variables and Primitives

##Variables

Using variables lets us write code that's easier to read and also easier to change. 

Suppose you want to log a set of greetings to the console:

```
console.log("Hi, Matt!");
console.log("How are you doing, Matt?");
console.log("See you later, Matt!");
```

What if we want to change the person's name from "Matt" to something else? We can just store a single copy of the name, and use it wherever we want. 

Variables give us this ability. In JavaScript, you initialize variables using the `var` keyword. Strictly speaking, is not necessary, but in practice it should almost always be there.

Let's rewrite the example above to use a variable:

```
var firstName = "Matt";
console.log("Hi, " + firstName + "!");
console.log("How are you doing, " + firstName + "?");
console.log("See you later, " + firstName + "!");
```

On the first line, we're declaring a variable using the var keyword. A variable is just a way for us to save some data.

We're using the `+` operator to combine words made up of characters, or strings, together. In JavaScript, when you combine two strings with the + operator, you get a new string which is a combination of the two. This is concatenation.

When declaring variables using multiple words, the standard is to capitalize each word after the first word, and otherwise use lower-case letters (e.g. firstName, not firstname, first_name, FirstName, or some other variation). This casing convention is called camel case.

##The `prompt` function

In JavaScript, you can ask the user to provide some information using the prompt function (there are better ways to get information from a user).

When you use the prompt function, a pop-up window will appear on the page and ask the user to fill in a text box. You can then store what the user types into a variable. 

```
var firstName = prompt("What is your first name?");
// Now firstName should correspond to whatever the user typed!
console.log("Hi, " + firstName + "!");
console.log("How are you doing, " + firstName + "?");
console.log("See you later, " + firstName + "!");
```

The two slashes indicate a comment. If you want a multiline comment:
```
/* this is the start of
a multiline comment, and
this is the ending. *
```

##Primitive Data Types in JavaScript

JavaScript has 6 primitive data types, but we'll only talk about 5 of them:

- string - `var greeting = "hello";`
- number - `var favoriteNum = 33;`
- boolean - `var isAwesome = true;`
- undefined - `var foo; or var setToUndefined = undefined;`
- null - `var empty = null;`

JavaScript is known as a "weakly" typed language: this means that when you create variables and assign them to values, you do not have to specify the type of data you are working with.

###string

A string is a set of characters enclosed in quotes. A string can be defined using double quotes or single quotes.

`var phrase = 'Matt said, "I haven\'t been to Chile", the other day.';`

The backslash is called an escape character and it tells JavaScript that the single quote in the string should not be used to end the string.

###number

JavaScript numbers can be positive, negative, decimal numbers and we can also do all of the math expressions you'd expect:

```
var x = 1 + 3;
var a = 4.5;
var b = 5.9;
var c = Math.sqrt(a * a + b * b);
var studentTeacherRatio = 4 / 1;
```

###boolean

A boolean type can only be in one of two states, true or false. Boolean types are a very useful tool for controlling our program. For example, if a user is signed in, you might want to show them a link to update their profile; but if a user is not logged in, you'd probably just want to show them a sign-in link. 

```
var pizzaIsGood = true;
var pizzaIsBad = false;
```

###undefined

Any variable that is created in JavaScript that is not assigned a value is undefined. You can also explicitly set a variable to undefined:
```
var noValue;  // The value here will be undefined

var favoriteFood = "Candy";
// Changed your mind
var favoriteFood = undefined;
```

###null

Null is not the same as undefined. It signifies an intentional absence of data.

`var secondEmailAddress = null;`

##Figuring out a variable's type in JavaScript

In JavaScript, we have a keyword called typeof that returns the type of the variable. 

`typeof "";` - "string"
`typeof 5;` - "number"
`typeof false;` - "boolean"
`typeof Symbol();` - "symbol"
`typeof undefined;` - "undefined"
`typeof null;` // hmmm, this is not what we expect, it returns "object"!

##Converting between types

Very often you'll need to convert a value from one type to another. In some cases JavaScript will change types implicitly, in a process that's often referred to as (implicit) type coercion.

Let's take a look at some ways to explicitly change the type of a value.

###Converting to a string: toString

The `toString` method will convert any value which is not undefined or null into a string.

```
var num = 5;
var bool = true;

num.toString(); // "5";
bool.toString(); // "true";
```

###Converting to a number

There are several ways you can convert a value to a number. One way is to parse the number, using parseInt or parseFloat: each function will look at a string from left to right and try to make sense of the characters it sees as numbers. 
```
parseInt("2"); // 2
parseFloat("2"); // 2
parseInt("3.14"); // 3
parseFloat("3.14"); // 3.14
parseInt("2.3alkweflakwe"); // 2
parseFloat("2.3alkweflakwe"); // 2.3
parseInt("w2.3alkweflakwe"); // NaN (not a number)
parseFloat("w2.3alkweflakwe"); // NaN (not a number)
```

The `Number` function doesn't parse, it simply tries to convert the entire directly to a number.
```
Number("2"); // 2
Number("3.14"); // 3.14
Number("2.3alkweflakwe"); // NaN 
Number("w2.3alkweflakwe"); // NaN
```

A nice shorthand for this conversion is the unary operator +:
```
+"2"; // 2
+"3.14"; // 3.14
+"2.3alkweflakwe"; // NaN 
+"w2.3alkweflakwe"; // NaN
```

###Converting to a boolean: `!!`

`!!` will convert a value to its boolean equivalent.
```
var greeting = "hi";
var nothing = 0;

!!greeting; // true
!!nothing; // false
```

