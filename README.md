## Scope, hoisting and compartmentalization

### Answer the following:
In you own words, explain the concepts of scope, hoisting, compartmentalization.

<!--SCOPE:-->

Javascript has two levels of scope, global and local. Global scope means that variables are accessible throughout the entire JS file, and can be used by any other element of the file. Local variables, however, only exist within the scope of a function, and cannot be accessed from outside the function that contains them.

<!--HOISTING-->

Javascript "hoists" variables and functions to the top of it's list, internally. It reads the document twice,
and prioritizes the variables and functions in order to allocate memory and optimize the program flow. You do not strictly need to do this in your code as JS will do it for you, but for readability and clarity of understanding for the user, best practice is to define variables and functions at the top of the document, which is where JS will do it anyway.

Problems can result if a function is called before it is defined, or variables are called upon before being given a value. So all of this should be done at the beginning before functions are called, so as not to return errors and wrong values.

<!--COMPARTMENTALIZATION-->

Compartmentalization is the practice of intentionally limiting the scope of variables, so as to not pollute
the global variables by changing them within a function. You treat data carefully and do not losely redefine global variables, preferring instead to use local scope variables within functions.

### Provide examples for all three, below:

#### Scope:

var dog = "puppy" <!-- this variable is global, not inside a function -->

function canine() {
	var dog = "wolf";  <!-- this one is local, and only exists inside the function -->
}

#### Hoisting:

<!--Below, line 38 is hoisted by javascript to be above line 37. This is an example of bad hoisting practice in my code, and z evaluates to equal 9. If lines 37 and 38 were swapped, the value would equal 11.-->

var x = 6;
y = 5;
var y = 3; 
var z = x + y;

#### Compartmentalization:

<!--The "cowColor variable is compartmentalized in the function, and doesn't affect the global scope.-->

var cowColor = "blue";

function redCow() {
  var cowColor = "red";
  console.log("This var cowColor is nested in the function and should appear Blue: " + cowColor);
}

redCow();
console.log("This cow should still be blue, because we compartmentalized the function variable: " + cowColor);

