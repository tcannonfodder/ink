# Native functions

_Functions call performed internally on behalf of the interpreter_

All function call _must_ be implemented.

## List of all native functions

_the number between parenthesis is the function's arity (number of parameters)_

**`+`** Add (2)

+ **If both operands are numbers**:
	* The return value is the sum. 
+ **If both operands are booleans, or if a boolean is added to a number**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is the sum.
+ **If one or both operands are strings**: 
	* The non-string operand is converted to its string representation (numbers as their decimal representation, `true` becomes `"true"` and `false` becomes `"false"`).
	* The return value is the concatenation of both string.
+ **If one of the operands is a `List` or a `List Item`**
	* It can't be mixed with non-list operands.
	* All `List Item` operands are considered as a `List` with only their item.
	* The return value is the union of both List.

**`-`** Subtract (2)

+ **If both operands are numbers**
	* The return value is the difference between the first and the second.  
+ **If both operands are booleans, or if a boolean is added to a number**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is the difference between the first and the second operand.
+ **If one of the operands is a `List` or a `List Item`**:
	* It can't be mixed with non-list operands.
	* All `List Item` operands are considered as a `List` with only their item. 
	* The return value is the first `List` with all element from the second removed.
+ **Subtract can't be applied to strings**


**`/`** Divide (2)

+ **If both operands are numbers**:
	* The return value is the division of the first by the second.  
	* If one of the two operands is a `FLOAT`, the result is a `FLOAT`; otherwise if the two operands are `INT`, the result is an `INT`.
		* Examples:

			```
			{13 / 3} // 4
			{13 / 3.0} // 4.3333335
			```

+ **If both operands are booleans, or if a boolean is added to a number:**
	* `true` is converted to `1` and `false` to `0`
	* The return value is the division of the first by the second operand.
+ **Dividing by zero causes a runtime error**.
+ **Divide can't be applied to string or Lists**

**`*`** Multiply (2)

+ **If both operands are numbers**:
	* The return value is the multiplication of the first by the second.  
	+ If one of the two operands is a `FLOAT`, the result is a `FLOAT`; otherwise if the two operands are `INT`, the result is an `INT`.
		* Examples:

			```
			{13 / (3 * 1)} // 4
			{13 / (3 * 1.0)} // 4.3333335
			```

+ **If both operands are booleans, or if a boolean is added to a number**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is the multiplication of the first by the second operand.
+ **Multiply can't be applied to string or Lists**

**`%`** Mod (2)

+ **If both operands are numbers**:
	* The return value is the rest of the euclidean division of the first by the second.
	+ If one of the two operands is a `FLOAT`, the result is a `FLOAT`; otherwise if the two operands are `INT`, the result is an `INT`.
		* Example:
			```
			{13 mod 5} // 3
			```
+ **If both operands are booleans, or if a boolean is added to a number**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is the rest of the euclidean division of the first by the second operand.
+ **Mod can't be applied to string or Lists**

**`_`** Negate (1)

+ **If the operand is a number**:
	* The return value is the opposite of it.
	+ If the operand is a `FLOAT`, the result is a `FLOAT`; otherwise if the operand is an `INT`, the result is an `INT`.
+ **If the operand is a boolean**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is the opposite of it.
+ **Negate can't be applied to string or Lists**

**`==`** Equal (2)
**`!=`** NotEquals (2)

+ **If both operands are numbers**
	* The return value is a boolean representing whether the first equals the second.
+ **If both operands are booleans, or if a boolean is added to a number**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is a boolean representing whether the first equals the second.
+ **If one or both operands are strings**:
	* The non-string operand is converted to its string representation (numbers as their decimal representation, `true` becomes `"true"` and `false` becomes `"false"`)
	* The return value is the equality between strings.
+ **If one of the operands is a `List` or a `List Item`**:
	* It can't be mixed with non-list operands.
	* All `List Item` operands are considered as a `List` with only their item.
	* The return value is a boolean that is true if and only if all elements from the first `List` are in the second `List` and all elements from the second `List` are in the first `List`.
+ **`NotEquals` always returns the inverse of `Equals`**

**`>`** Greater (2)  
**`<`** Less (2)  
**`>=`** GreaterThanOrEquals (2)  
**`<=`** LessThanOrEquals (2)  

+ **If both operands are numbers**
	* The return value is a boolean representing how the first compares to the second.  
+ **If both operands are booleans, or if a boolean is added to a number**:
	* `true` is converted to `1` and `false` to `0`
	* The return value is a boolean representing how the first compares to the second.
+ **Comparisons can't be applied to strings.**
+ **If one of the operands is a `List` or a `List Item`**
	* It can't be mixed with non-list operands.
	* All `List Item` operands are considered as a `List` with only their item. 
	+ `>` is true between `Lists` if the value of the smallest element of the first `List` is strictly greater than the value of the biggest element of the second `List`.
	+ `>=` is true between `Lists` if the value of the smallest element of the first `List` is greater or equal than the value of the smallest element of the second `List` _and_ if the value of the biggest element of the first `List` is greater or equal than the value of the biggest element of the second `List`.
	+ `<` is true between `Lists` if the value of the biggest element of the first `List` is strictly less than the value the smallest element of the second `List`.
	+ `<=` is true between `Lists` if the value of the biggest element of the first `List` is less or equal than the value of the biggest element of the second `List` _and_ if the value of the smallest element of the first `List` is less or equal than the value of the smallest element of the second `List`.

**`!`** Not (1)

+ **If the operand is a number**:
	* Returns `true` if its value is not zero.
+ **If the operand is a boolean**
	* Returns the opposite.
+ **If the operand is a `List`**:
	* Returns `true` if its count is not 0.
+ **`Not` can't be applied to strings.**

**`&&`** And (2)  
**`||`** Or (2)

+ All non-boolean operands are first converted to boolean
	* non-zero number, non-empty `Lists` and non-empty strings are converted to `true` otherwise to `false`
+ The return value is the result of the boolean.

**`MIN`** Min (2)
**`MAX`** Max (2)

**`POW`** Pow (2)

**`FLOOR`** Floor (1)

**`CEILING`** Ceiling (1)

**`INT`** Int (1)

**`FLOAT`** Float (1)

**`?`** Has (2)

**`!?`** Hasn't (2)

**`L^`** or **`^`** Intersect (2)

**`LIST_MIN`** ListMin (1)

**`LIST_MAX`** ListMax (1)

**`LIST_ALL`** All items (1)

**`LIST_COUNT`** Count (1)

**`LIST_VALUE`** ValueOfList (1)

**`LIST_INVERT`** Invert (1)