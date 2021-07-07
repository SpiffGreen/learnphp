# Learn PHP
------------------------------------
<!-- Use php description from wikipedia -->
### PHP is a general-purpose scripting language especially suited to web development. It was originally created by Danish-Canadian programmer Rasmus Lerdorf in 1994.
### PHP originally stood for Personal Home Page, but it now stands for the recursive initialism PHP: Hypertext Preprocessor.. PHP code is usually processed on a web server - [WikiPedia](https://en.wikipedia.org/wiki/PHP)
------------------------------------
## Introduction
This repository is intended to be a simple goto resource for learning and getting along the PHP road fast.

## Table Of Content
* Getting Started With PHP - PHP syntax
* Variables, Variable Scope, Constants and Magic Constants
* Comments
* SuperGlobals
* PHP Input/Output
* PHP Data Types
* Operators and References
* Arrays
* Control Structures
* Loops
* Functions
* Dates and Time
* Classes And Objects
* Namespaces
* Sessions
* Cookies
* JSON
* SOAP Client
* Using CURL in PHP
* XML and HTML Parsing
* Regular Expressions(regex)
* Magic Methods
* File Handling
* Streams in PHP
* Filter Functions and Generators
* Exception Handling and Error Reporting
* UTF-8
* URLs
* Object serialization
* Closure
* Reading Request Body
* Sockets
* PDO, MySqli and SQlite3 (Database operations in PHP)
* Mailing with PHP
* PHP CLI
* Headers Manipulation
* Create PDF Files
* Image Processing with PHP
* Machine Learning with PHP
* Caching
* HTTP Authentication
* Coding Conventions
* Design Patterns
* PHP Code Documentation and Unit Testing
* Multiprocessing and Multi-threading
* Security and Cryptography
* References
---------------------------------------------------
## Chapter 1: Getting Started With PHP - PHP Syntax
PHP is a very powerful language used for server side programming in making dynamic content, e.g websites whose contents are different based on the users, authentication, authorization, etc
It's syntax is pretty simple and straight forward. PHP files are with an extension .php, .phpt, etc. The most common of which is .php. The file content is allowed to contain html, this isn't a problem since the output given by the web server that runs a PHP script is html.
The actual PHP codes are enclosed within `<?php...?>` tags, i.e it starts with `<?php` and ends with `?>`. E.g
```php
  <?php
    echo "Hello World";
  ?>
```
PHP codes are made of program statements and expressions. In PHP all statements must be terminated with semi-colon(`;`). The `echo` keyword in the above example is a language construct used to output text. More on that in I/O Section.
To run PHP code we need either a web server or the PHP CLI tool.
For the CLI tool simply run `php file.php` in the terminal.

## Chapter 2: Variables, Variable Scope, Constants and Magic Constants
Variables are one of the fundamental building blocks of computer programs, many programming languages exhibit this concept and PHP is no exception. Variables are like memory boxes. Imagine having a box where you store something inside and give it a label, whenever you want to use it you simply pass the label of the box. In programming this boxes are referred to as variables and are very helpful for holding values for us. In PHP we don't have to specify the type of data to be stored in the variable like in other languages - this means PHP is dynamically typed. Variables in PHP are also preceded with the dollar sign `$`.
Syntax - `$variable_name = value;`

### Rules for PHP variables
\-  A variable name must start with a letter or an underscore <br>
\-  A variable name cannot start with a number <br>
\-  A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _) <br >
\-  Variable names are case-sensitive ($age is not same as $Age or $AGE)

For Example:
```php
  <?php
    $name = "John Doe";
    $age = 21;
    echo "Hi my name is $name, I am $age years old";
    // outputs "Hi my name is John Dow, I am 21 years old"
  ?>
```
Note: As you can see from the above example, PHP allows placing variables in strings, but this is specific to double quoted strings.

### Variable variables
In PHP you can use the content of one variable to specify the content of another variable's name. Example:
```php
  <?php
    $a = "doe";
    $doe = "I'm John Doe";
    echo $$a; // Outputs "I'm John Doe"
  ?>
```

### Constants
Contants are similar to variable except that their values cannot be changed or undefined after they've been defined. In PHP constants are created using the define function, which takes two required parameters and on optional parameter.

Syntax - `define(name, value, case=insensitive);` 

Here name specifies the name of the constant, PHP doesn't require the constants'name to be preceded by a dollar sign.

Example:
```php
  <?php
    define("ID", "This is a constant");
    echo ID;
  ?>
```

### Variable Scope
Variable Scope simply refer to the space or area of code where a variable exists. Example
```php
  <?php
    function greet() {
      $greeting = "Hello dear";
      echo $greeting;
    }
    greet();
    echo $greeting; // This would cause an error
  ?>
```
The above code won't work as the variable $greeting is defined in the function greet and is not accessable outside the function. This is seen in other programming languages too. But one thing that not so common in general programming languages that PHP exhibits is the fact that variables declared outside of function are not accessible within functions defined in their scope except explicitly defined, this is done using the GLOBAL keyword. See example below:
```php
  <?php
    $fav_color = "green";
    function print_fav_color() {
      GLOBAL $fav_color;
      echo $fav_color; // prints the content of $fav_color variable without erros since tre 
    }
    print_fav_color();
  ?>
```

## Chapter 3: Comments
You may have noticed lines of code containing double slashes `//`. Parts of code after this are not executed and are simply ignored by the compiler/interpreter doing code execution. These are known as comments and are used by programmers to make notes about the written code.
### Types of Comments
* Single line comments e.g 
```php
  <?php
    // Code after this is not executed until the end of the line
    # This is also a single line comments
  ?>
```
* Multi-line comments - These comments can span multiple lines e.g
```php
  <?php
    /* 
      Anything that goes in here will not be executed
      And this can span multiple lines    
    */
  ?>
```


## Chapter 4: Superglobal Variables in PHP
Superglobals are built-in variables that are always accessible in all scopes throughout a PHP script. This means you don't have to do `global $variable` to make them available to your code. As of `PHP >= 7.x` there are now 9 superglobal variables available. They include:
* `$GLOBALS` -  This is simply an associative array containing references to all global variables in a script
* `$_SERVER` -  This contains server and environment information such as headers, paths, etc
* `$_GET` - HTTP Get variables. Its also an associative array of variables. The keys and their values are passed in the url e.g `http://example.com/index.php?name=john&age=21` name and age will be keys in the $_GET associative array
* `$_POST` -  HTTP POST variables. An associative array of variables passed to the current script via the HTTP POST method. The values passed are gotten via name fields in HTML input forms or json format
* `$_FILES` - HTTP File upload variables. An associative array of items uploaded to the current script using the POST method
* `$_COOKIE` - HTTP Cookie. Still Another associative array of variables passed to the current script via HTTP Cookies. Cookies are created/set using the `setcookie(name, val, exp)` function where name refers to the name of the cookie, val the value, and exp refer to the time the cookie expires. The cookies are stored on the users computer.
* `$_SESSION` - Session Cookie. This is an associative array containing variables. Session cookies are stored on the server.
* `$_REQUEST`  - HTTP Request variables. This associative array by default contains the contents of $_GET, $_POST AND $_COOKIE.
* `$_ENV` - This contains environment variables. An associative array passed to the script via the environment method.

## Chapter 5: PHP Input/Output
<!-- Content Not Yet Ready -->
...
## Chapter 6: PHP Data Types
There are basically 8 data types available which include:
* Boolean
* Float
* Integer
* String
* Null
* Array
* Object
* Resource
### `Boolean`
Represents two possible state: TRUE or FALSE.
```php
  <?php
    $x = true; $y = false;
  ?>
```
They are often used in conditional testing.
```php
  <?php
    $x = false;
    if($x) echo "Yes x is false"; // Echo isn't executed
  ?>
```

### `Float`
Floats or floating point numbers are numbers which allow more output precision than plain integers. These are numbers that include decimal point. e.g `$x = 3.142`

### `Integer`
Integers are whole numbers, without a decimal point. e.g `234 `.

### `Strings`
Strings are sequences of characters, like `'hello world'`, enclosed in quotes/double quotes.

### `NULL`
NULL is a special type PHP gives us. It only has one value: NULL. Variables assigned the value of null will evaluate to False in boolean expressions.
Syntax - `$var = NULL` or `$var = null`. The value null is case insensitive.

### `Array`
Arrays are named indexed collections of other values. Example
```php
  <?php
    $arr1 = [1, 2, 3, 4]; // numerically named arrays
    $arr2 = [
      "one" => 1,
      "two" => 2
    ]; // Associative arrays
    $arr3 = array(1, 2, 3, 4); // Use of array method for creating arrays
    $arr4 = array(
      "one" => 1,
      "two" => 2
    );
  ?>
```
Few array methods include `reverse()`, `implode()`, `sort()`, etc.

### `Object`
Objects are instances of programmer-defined classes, which can package up both other kind of values and functions that are specific to the class. Its considered a compound type.

### `Resources`
Resources are special values that hold references to resources external to PHP (such as database connections). Its considered a compound type too.

## Chapter 7: Operators and References
Consider the expression `2 + 3`. Here `2` and `3` are called operands and `+` is called the operator. The operator defines what kind of operation to be performed on the operands. PHP supports 5 kinds of operators. They include:
* Arithmetic Operators
* Comparison Operators
* Logical (or Relational) Operators
* Assignment Operators
* Conditional (or tenary) Operators

### Arithmetic Operators
PHP supports the following arithmetic operators: __plus(+), minus(-), multiplication(*), division(/), modulus(%), increment(++), decrement(--)__.

### Comparison Operators
PHP supports the following comparison operators: __==, ===, !=, >, <, >=, <=__.

### Logical Operators
PHP supports the following logical operators: __and, or, &&, ||, !__.

### Assigment Operators
The following assignment operators are supported in PHP: __=, +=, -=, *=, /=, %=__.

### Conditional Operator
This operator will first evaluate an expression for a boolean value and then execute one of the two given statements depending on the result of the expression. Syntax `(condition) ? statement1 : statement2`. If condition when evaluated results to true, statement1 will be executed else statement2 will be executed.

See More - [Operator Precedence](), [Operator Categories]()

### References
* Assigning By Reference
When you assign by reference, you're allowing two variables share the same memory location. Hence they will have same value but it doesn't mean they point to one another. Example use case for assigning by reference:
```php
  <?php
    /* incrementing the value of each element in an array */
    function add_one(&$arr) {
      foreach($arr as &$val) {
        $val++;
      }
    }

    $arr = array(1, 2, 3, 4, 5);
    add_one($arr);
    print_r($arr);

    /* variable swapping */
    $x = 1;
    $y = 2;
    
    function swap(&$a, &$b) {
      $temp = $a;
      $a = $b;
      $b = $temp;
    }

    echo "Before Swap: x: $x, y: $y\n";
    swap($x, $y);
    echo "After Swap: x: $x, y: $y\n";
  ?>
```
* Return and Pass By Reference
To from a function by reference, we simply precede the function name with the ampersand symbol in the function definition. Example
```php
  <?php
    function &addAge($val = 0) {
      static $age;
      $age += $val;
      return $age;
    }

    function changeAge(&$age, $newAge) {
      $age = $newAge;
      echo "New age: ".$age;
    }

    echo addAge(10)."\n";
    echo changeAge(addAge(), 2)."\n";
    echo addAge();
  ?>
```

## Chapter 8: Arrays
An array is a data structure that stores an arbitrary number of values in a single value.
Initializing an array in PHP follows the syntax below:
```php
  <?php
    /* Without values */
    $arr = array();
    // or
    $arr = [];

    /* With values */
    $arr = array("dig", "big", "gig", "did"); // array with four strings
    // or
    $arr = ["dig", "big", "gig", "did"]; // shorthand notation
  ?>
```
### Associative Arrays
PHP gives the programmer the ability to customize indexes of an array. Arrays like this are called associative arrays. Example:
```php
  <?php
      $numbers = array(
        "one" => 1,
        "two" => 2,
        "three" => 3,
        "four" => 4
      );
  ?>
```
