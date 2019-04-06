#Boolean Logic

An essential part of writing programs is being able to execute code that depends on certain conditions. To write conditional logic in JavaScript we'll make use of booleans (`true` and `false`), along with `if` statements and `switch` statements.

An if statement looks something like this:

```
var instructor = "Elie";

// we begin with an "if" statement followed by a condition in () and a block of code inside of {}
if(instructor === "Elie") {
    console.log("Yes!");
} else {
    console.log("No");
}
```

We used a `===` instead of `=`. Anytime that we use more than one equals operator (we can either use `==` or `===`) we are comparing values. When we use a single equals operator `=`, we are setting a variable equal to some value.

##Difference between `==` and `===`

In JavaScript we have two different operators for comparison: the double and triple equals. `==` allows for type coercion of the values, while `===` does not. So to understand the difference between these operators, we first need to understand what is meant by type coercion.

```
// 1.
5 + "hi"; // "5hi"

// 2.
if ("foo") {
  console.log("this will show up!");
}

// 3.
if (null) {
  console.log("this won't show up!");
}

// 4.
+"304"; // 304
```

In the first example you've asked JavaScript to add a number and a string. It evaluates the expression 5 + "hi" by first coercing 5 into a string, and then interpreting the "+" operator as string concatenation.

The next two examples show a similar sort of coercion. JavaScript expects the values inside of parentheses that come after the keyword if to be booleans. If you pass in a value which is not a boolean, JavaScript will coerce the value to a boolean according to the rules for truthy/falsey values.

The last example shows a very common way to coerce a stringified number back into a number. 

Coercion is just the process of converting a value from one type to another.

```
5 == "5"; // true
5 === "5"; // false
"true" === true; // false
"true" == true; // false
true == 1; // true
true === 1; // false
undefined === null; // false
undefined == null; // true
```

Let's deal with the expressions involving `===` first. All evaluate to false: none of the values being compared are the same. 

The `==` operator is a little less strict (in fact, `===` is sometimes referred to as the "strict" equality operator, while `==` is sometimes referred to as the "loose" equality operator). The reason that comparisons like `5 == "5"` evaluate to true is because `==` allows for type coercion.

##If / else statements with other comparators

```
var x = 4;
if(x <= 5){
    console.log("x is less than or equal to five!");
} else {
    console.log("x is not less than or equal to five!");
}
```
We `==` or `===` to compare values. We can also check for inequality, using

`<` - less than,

`<=` - less than or equal to,

`>` - greater than,

`>=` - greater than or equal to,

`!=` - not equal (loose), and

`!==` - not equal (strict).

##Falsey Values

In JavaScript some values (aside from false) are actually false as well when they're used in a context where JavaScript expects a boolean value.

There are 6 falsey values:

- `0`
- `""`
- `null`
- `undefined`
- `false`
- `NaN` (short for not a number)

If you ever want to determine if a value is truthy or falsey, you can prefix it with !!. !! explicitly coerces a value into its boolean form.

##!, || and &&

In our conditions we can use certain logical operators to write more complex statements:

`!` - the not operator, which flips the boolean value (`!true === false`). `!!` simply applies this operator twice, so `!!true === true`, and `!!false === false`.

`||` - the or operator, which in a boolean context returns true if either condition is true

`&&` - the and operator, which in a boolean context returns true if both conditions are true

##Ternary Operators

A ternary operator is another way to write an if / else statement. 
```
var guess = prompt("Guess what number I'm thinking of!");

if (guess === "7") {
    console.log("Correct!");
} else {
    console.log("Incorrect!");
}
```

You could refactor this code using a ternary operator:

```
var guess = prompt("Guess what number I'm thinking of!");

// here's our first ternary
guess === "7" ? console.log("Correct!") : console.log("Incorrect!");
```

In general, a ternary operator has the form:

`expression ? pathIfTrue : pathIfFalse`

You can also store the value of a ternary in a variable:
```
var num = 3;
var comparison = num > 0 ? "Greater than 0" : "Less than or equal to 0";
comparison; // this will equal "Greater than 0", since 3 > 0.
```

##If / else if / else

Sometimes you may have more than two conditions to check:

```
var number = prompt("What's your favorite number?");

if (number >= 1000) {
    console.log("Woah, that's a big number!");
} else if (number >= 0) {
    console.log("That's a cool number.");
} else {
    console.log("Negative numbers?! That's just bananas.");
}
```

##Switch statements

Another way to write conditional logic is to use a switch statement. Each case clause needs to end with a break so that we exit the switch statement.

```
var feeling = prompt("How are you feeling today?").toLowerCase();
// what do you think the .toLowerCase does at the end?

switch(feeling){
    case "happy":
        console.log("Awesome, I'm feeling happy too!");
        break;
    case "sad":
        console.log("That's too bad, I hope you feel better soon.");
        break;
    case "hungry":
        console.log("Me too, let's go eat some pizza!");
        break;
    default:
        console.log("I see. Thanks for sharing!");
}
```

##Modulus Operator

The modulus operator returns the remainder of a number when dividing by another number. 

```
var num = prompt("Please enter a whole number");
if ( num % 2 === 0 ) {
    console.log("the num variable is even!")
} else if ( num % 2 === 1) {
    console.log("the num variable is odd!")
} else {
    console.log("Hey! I asked for a whole number!");
}
```
