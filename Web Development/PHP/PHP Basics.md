- [Hello, World!](#hello-world)
- [Variables and Types](#variables-and-types)
  - [Operators](#operators)
  - [String Formatting](#string-formatting)
- [Arrays](#arrays)
  - [Array Functions](#array-functions)
  - [Stack and Queue Functions](#stack-and-queue-functions)
  - [Concatenating Arrays](#concatenating-arrays)
  - [Sorting Arrays](#sorting-arrays)
  - [Advanced Array Functions](#advanced-array-functions)
- [Arrays with Keys](#arrays-with-keys)
- [Strings](#strings)
  - [Joining and Splitting](#joining-and-splitting)
- [For Loops](#for-loops)
  - [Foreach Loops](#foreach-loops)
- [While Loops](#while-loops)
  - [Flow Statements](#flow-statements)
- [Functions](#functions)
- [Objects](#objects)
  - [Inheritance](#inheritance)
  - [Public and Private](#public-and-private)
- [Exceptions](#Exceptions)


# Hello, World!

PHP is one of the most commonly used programming langauges on the web because of its realtively simple architecture compated to other MVC (model view controller) based web frameworks.

Unlike standard frameworks, PHP is an "enhanced" HTML file, which is also capable of executing code inside a document.

PHP code is place inside plain HTML text and wrapped in `<?php ?>` tags. The code inside is run and replaced with HTML when the file is used.

```php
<?php $user = "John"; ?>
<html>
  <head></head>
  <body>
    <h1>Hello, <?php echo $user; ?>!</h1>
  </body>
</html>
```

This will display our `h1` header as "Hello, John". These notes will focus on PHP as a language though, and not focus on the web development aspect yet. We will write code, not web pages.

# Variables and Types

Variables are defined by starting the variable name with a dollar symbol (`$`), and assigning a value.

```php
$x = 1;
$y = "foo";
$z = True;
```

The basic variable types in PHP are intergers, float values, strings, and booleans. PHP also has arrays, objects, and `NULL`.

## Operators

We can use regular operators to perform math with variables.

```php
$x = 1;
$y = 2;
$sum = $x + $y;
echo $sum; // prints 3
```

## String Formatting

We can use variables in strings very simply:

```php
$name = "Aaron";
echo "Hello, $name"; // prints "Hello, Aaron
```

# Arrays

Simple arrays are defined using square brackets (`[]`). Accessing indexes works similar to other langauges.

```php
$odd_numbers = [1,3,5,7,9];
$first_odd_number = $odd_numbers[0]; // stores 1
```

To remove items from an array, we use the `unset()` function and pass the value or `array[index]` to remove.

```php
$odd_numbers = [1,3,5,7,9];
unset($odd_numbers[2]); // removes 5 from the array
```

## Array Functions

`count()` returns the number of members in an array.

```php
$odd_numbers = [1,3,5,7,9];
echo count($odd_numbers); // prints 5
```

`reset()` gets the first memeber of the array and resets the internal iteration pointer.

```php
$odd_numbers = [1,3,5,7,9];
$first_item = reset($odd_numbers);
echo $first_item; // prints 1
```

`end()` gets the last member of an array

```php
$odd_numbers = [1,3,5,7,9];
$last_item = end($odd_numbers);
echo $last_item; // prints 9
```

## Stack and Queue Functions

`array_push()` takes two arguments, the array to use and value to add to the end of the array.

```php 
$numbers = [1,2,3];
array_push($numbers, 4); // -> [1,2,3,4]
print_r($numbers); // prints the new array
```

`array_pop()` will remove the last item in an array.

```php
$numbers = [1,2,3];
array_pop($numbers); // -> [1,2]
```

`array_unshift()` will instert an item at the beginning of an array.

```php
$numbers = [1,2,3];
arrau_unshift($numbers, 0); // -> [0,1,2,3]
```

`array_shift()` will remove the first element of an array.

```php
numbers = [1,2,3];
array_shift($numbers); // -> [2,3]
```

## Concatenating Arrays

We can use `array_merge()` to concatenate arrays.

```php
$odd_numbers = [1,3,5,7,9];
$even_numbers = [2,4,6,8,10];
$all_numbers = array_merge($odd_numbers, $even_numbers);
```

## Sorting Arrays

We can use `sort()` to sort an array or `rsort()` to sort an array in reverse order.

```php
$numbers = [4,2,3,1,5];
sort($numbers); // -> [1,2,3,4,5]
```

## Advanced Array Functions

`array_slice()` returns a new array that contains a specific part of the oringal array and removes that section from the original array. It takes 3 arguments: 

1. The array to be used
2. The index to start on
3. The length of the slice (optional, default 1)

```php
$numbers = [1,2,3,4,5,6];
$sliced_numbers = array_slice($numbers, 3, 2); // -> [5,6]
// $numbers is now [1,2,3,4]
```

# Arrays with Keys

PHP arrays are actually ordered maps, meaning that all values of arrays have keys, and the items inside the array preserve order. By default, a zero based counter is used to set keys, making are keys numerical starting at 0. Every item added increments the counter.

A good example of setting out keys manually in an array is when we store something like phone numbers:

```php
$phone_numbers = [
  "Alex" => "415-235-8573",
  "Jessica" => "415-492-4856",
];

print_r($phone_numbers);
echo "Alex's phone number is " . $phone_numbers["Alex"] . "\n";
echo "Jessica's phone number is " . $phone_numbers["Jessica"] . "\n";
```

To add items to an array using a key, we use square brackets:

```php
$phone_numbers["Michael"] = "415-955-3857";
```

We can use `array_key_exists()` to determine if an array has a specific key.

```php
if (array_key_exists("Michael", $phone_numbers)) {
    echo "Michael's phone number is " . $phone_numbers["Michael"] . "\n";
} else {
    echo "Michael's phone number is not in the phone book!";
}
```

If we only want to extract the keys of an array, we can use `array_keys()`

```php
print_r(array_keys($phone_numbers));
```

Alternatively, to only get the values, we use `arra_values()`

```php
print_r(array_values($phone_numbers));
```

# Strings

Strings can be concatenated using the dont (`.`) operator

```php
$first_name = "John";
$last_name = "Doe";
$name = $first_name . " " . $last_name;
echo $name; // prints "John Doe"
```

We can get the length of the string with the `strlen()` function.

```php
echo strlen($string);
```

We can cut part of a string and return a new string if we use `substr()`

```php
$filename = "image.png";
$extension = substr($filename, strlen($filename) - 3);
echo "The extension of the file is $extension";
```

## Joining and Splitting

Splitting strings is done with the `explode()` method. It takes to arguments:

1. The character to split at
2. The string to split

```php
$fruits = "apple,banana,oragne";
$fruit_list = explode(",", $fruits);
```

Joining an array to a string works the exact same using the `implode()` method.

```php
$fruit_list = ["apple", "banana", "orange"];
$fruits = implode("," $fruit_list);
```

# For Loops

For loops work the same way as other programmig languages:

```php
$odd_numbers = [1,3,5,7,9];
for ($i = 0; $i < count($odd_numbers); $i++) {
  $odd_number = $odd_number[$i];
  echo $odd_number . "\n";
}
```

## Foreach Loops

Foreach loops also work in the same way as other languages:

```php
$odd_numbers = [1,3,5,7,9];
foreach ($odd_numbers as $odd_number) {
  echo $odd_number . "\n";
}
```

When iterating over arrays with keys, we can use the following:

```php
$phont_numbers = [
  "Alex" => "415-235-8537",
  "Jessica" => "415-492-4856"
];

foreach ($phone_numbers as $name => $number) {
  echo "$name's number is $number.\n";
}
```

# While Loops

While loops work the same way as with other programming languages:

```php
$counter = 0;

while ($counter < 10) {
  $counter += 1;
  echo "Counter is $counter.\n"
}
```

## Flow Statements

Loops can be controlled using the `break` and `continue` flow statements. `break` will immediately quit the loop in the middle of the block while `continue` returns to the top of the `while` loop and rechecks the conditional of the loop.

```php
// Using the continue flow statement
$counter = 0;

while ($counter < 10) {
  $counter += 1;

  if ($counter % 2 == 0) {
    echo "Skipping even number: $counter \n";
    continue;
  }

  echo "Executing - countis is $counter \n";
}
```

```php
// Using the break flow statement
$counter = 0;

while ($counter < 10) {
    $counter += 1;

    if ($counter > 8) {
        echo "counter is larger than 8, stopping the loop.\n";
        break;
    }

    if ($counter % 2 == 0) {
        echo "Skipping number $counter because it is even.\n";
        continue;
    }

    echo "Executing - counter is $counter.\n";
}
```

# Functions
Functions are defined with the `funciton` token.

```php
// define a function called `sum` that will
// receive a list of numbers as an argument.
function sum($numbers) {
    // initialize the variable we will return
    $sum = 0;

    // sum up the numbers
    foreach ($numbers as $number) {
        $sum += $number;
    }

    // return the sum to the user
    return $sum;
}

// Example usage of sum
echo sum([1,2,3,4,5,6,7,8,9,10]);
```

# Objects

PHP is object oriented. Objects are defined by using the `class` token. Constructor funcitons are defined uising `public function __construct()` and the object is referenced with the `$this` variable followed by `->`.

```php
class Student {
  // constructor
  public function __construct($first_name, $last_name) {
    $this->first_name = $first_name;
    $this->last_name = $last_name;
  }

  public function say_name() {
    echo "My name is " . $this->$first_name . " " . $last_name . ".\n";
  }
}

$alex = new Student("Alex", "Jones");
$alex->say_name();
```

***From here, I assume that PHP doesn't use dot notation to access object specific methods, instead using `->`. Also, with the use of `public`, I assume there are other scope keywords such as `private`***

## Inheritance

We can use inheritance and extend classes with the `extends` token.

```php
class Student {
    // constructor
    public function __construct($first_name, $last_name) {
        $this->first_name = $first_name;
        $this->last_name = $last_name;
    }

    public function say_name() {
        echo "My name is " . $this->first_name . " " . $this->last_name . ".\n";
    }
}

$alex = new Student("Alex", "Jones");
$alex->say_name();

// MathStudent inherits from Student
class MathStudent extends Student {
    function sum_numbers($first_number, $second_number) {
        $sum = $first_number + $second_number;
        echo $this->first_name . " says that " . $first_number . " + " . $second_number . " is " . $sum;
    }
}

$eric = new MathStudent("Eric", "Chang");
$eric->say_name();
$eric->sum_numbers(3, 5);
```

## Public and Private

We do have scope tokens! We can use `private` and `public` to define funcitons that can be used outside of the object or only inside the object. Any function marked as `private` cannot be used on or outside of the object, but funcitons marked as `public` can.

```php
class Student {
    // constructor should be public
    public function __construct($first_name, $last_name) {
        $this->first_name = $first_name;
        $this->last_name = $last_name;
    }

    // for external use
    public function say_name() {
        echo "My name is " . $this->full_name() . "\n";
    }

    // for internal use
    private function full_name() {
        return $this->first_name . " " . $this->last_name;
    }
}

$alex = new Student("Alex", "Jones");

$alex->say_name();

// this will not work
// echo $alex->full_name();
```

# Exceptions

PHP has exception models similar to other programming languages. We can use `try`/`catch` blocks to catch exceptions.

```php
try {
  echo 2 / 0;
} catch (Exception $e) {
  echo "Caught exception: Division by zero!";
}
```

We can also create our own exceptions:

```php
if (4 / 2 == 2) {
  echo "Right!";
} else {
  throw new Exception("Wrong answer!");
}
```

We can use finally at the end of try/catch blocks to have code that will always be exectued after the try/catch block, regardless of whether or not an exception has been thrown, and before normal execution resumes.

```php
try{
  echo 4 / 0;
} catch (Exception $e) {
  echo "Divided by zero!";
} finally {
  echo "This is outputed regardless of exception.";
}
```
