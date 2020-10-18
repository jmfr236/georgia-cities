# Quiz-02
## MAP672, Fall 2020
1. Operators behave differently on different data types. A plus sign operator will result in a different outcome when applied to string values than numeric values.

2. It is recognizing 3 + 5 as numeric values and "8" as a string. So calculating 3+5=8 and concatenating the string "8" at the end.

3. Single equal sign = differs from a double equal sign ==. Single equal sign is an assignment operator (ex: city = "Lexington"). In the instance above should use double equal sign and it will convert to number.

<!-- Also, a variable name cannot start with a number. -->

4.  Example JS

``` js
  var myMap = ["map","thousand","is","A","worth","a","pictures","."];
 console.log(myMap[3]); // outputs the String "A"
 console.log(myMap[0]); // outputs the String "map"
 console.log(myMap[2]); // outputs the String "is"
 console.log(myMap[4]); // outputs the String "worth"
 console.log(myMap[5]); // outputs the String "a"
 console.log(myMap[1]); // outputs the String "thousand"
 console.log(myMap[6]); // outputs the String "pictures"
 console.log(myMap[7]); // outputs the String "."


var words = ["map","thousand","is","A","worth","a","pictures","."];
// Example using a template string, which was introduced after you took the course.
// 
var sentence = `${words[3]} ${words[0]} ${words[2]} ${words[4]} ${words[5]} ${words[1]} ${words[6]}${words[7]}`;
console.log(sentence);

```


## Concatenating strings and template literals

As we dynamically create content (e.g., for popups), we will rely on combining bits of data into readable strings. As we have discovered this is called *concatenation*, and we can use the addition `+` operator on string literals, expressions, and variables. In the example below, we are combining an expression `(31 - 13)`, a string literal, and a variable.

```javascript
var costume = "my 🐩 needs a costume"
var newString = (31 - 13) + "days until Halloween" + costume
console.log(newString)
```

The Console should print the following.

```js
18days until Halloweenmy 🐩 needs a costume
```

We have a number of issues with formatting that make the string slightly annoying, e.g., missing spaces between words and no punctuation. We can add the spaces and new variables in a somewhat verbose fashion. 

```javascript
var costume = "my 🐩 needs a costume"
var space = " "
var period = "."
var and = "and"
// Build string without altering the original data
var newString = (31 - 13) + space + "days until Halloween" + space + and + space + costume + period
// Alternative version that changes the string literal
var altVersion = (31 - 13) + " days until Halloween and " + costume + "."
console.log(newString)
```

OK, we fixed the problem with two versions. The syntax relies on the addition `+` operator to concatenate every bit of data into a single string. But, it's also a math operator and can be used in the same statement. Confusing? Of course, it is! 

Wouldn't it be easier to remove the `+` string operator and *embed* your variables and expressions in a string? We can use the [*template literals*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)  (often called *template strings*) to make string concatenations more easy to read and construct. In this method, the `+` operator will always be recognized as a math operator.

In the traditional method of declaring a string, we've enclosed values in single or double quotes. A template literal uses the backtick, \` (which is the key to the left of the number `1` key), to enclose the string. To embed variables and expressions in the string, wrap them in the dollar sign and curly brackets, `${ }`. The above statement would be rewritten as:

```javascript
var costume = "my 🐩 needs a costume"
var newString = `${(31 - 13)} days until Halloween and ${costume}!`
console.log(newString)
```

Much easier to read! You will find that constructing template literals will be more concise and easier to manage than traditional string concatenation with the `+` operator. This feature was adopted in the JavaScript standard defined in JS version 6 (often called ES6 for ECMAScript 6 or, confusingly ECMA2015, because it was adopted in 2015). Every major browser, except Internet Explorer, supports template strings. IE's replacement, Edge, does support this.

Since 2002, [w2schools](https://www.w3schools.com/browsers/) has tracked browser use on their site. One can clearly observe the precipitous decline in some browsers over the years. Also check out the [Can I Use](https://caniuse.com/#search=template%20strings) website validate that your browser can use specific JS features. If you are targeting the most popular browsers, you can use new features without much worry. Over the next few modules, we'll introduce some new features that you could adopt in your project for these popular browsers. 

OK, what else can template stings do if I adopt their use, you ask? If you need to make a multi-line string to avoid a very long single line (helps with readability), template strings make it much (much!) easier. Consider this syntax.

```js
var htmlCode = `<div>
                    <h2>Welcome!<h2>
                    <ul>
                     <li>This is an unordered list</li>
                     <li>with three items</li>
                     <li>on a multi-line template string</li>
                    <ul>
                </div>`
console.log(htmlCode)
```

If you decide to use template literals, just remember that if you need to use a backtick character and/r the `${}` sequence in a string (unlikely), you must escape them with the backslash `\` character. For example,

```javascript
var word = "days until Halloween"
var day = new Date()
console.log(day)
if (day.getMonth() == 9) {
    var daysUntil = 31 - day.getDate();
} else {
    var daysUntil = "not October! Think of a different holiday! Too many"
}
var newString = `\${Scary syntax} & backticks \`\` tell us it's ${daysUntil} ${word}.`
console.log(newString)
```

In the above example, we introduce some new material that we'll address in much more detail soon. The `var day = new Date()` constructs a new date object and stores it as a variable. We can then access properties of the date object with a special syntax, i.e., get the month with `.getMonth()` and the day of the month with `.getDate()` methods. For now, see what other dates you can test and output the results in template strings.