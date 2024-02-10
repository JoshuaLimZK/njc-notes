#computing
[[Computing]]

# 6 Program Testing and Data Validation

# 6.1 Errors

Types of errors:
- Syntax errors
- Static semantic errors
- Logic errors
- Arithmetic errors

Some of the above errors are also under the category of **runtime errors**

>[!info] Runtime Errors
> Errors that occur during the execution of a program

## 6.1.1 Syntax Errors

>[!info] Syntax Errors
> Errors that occur when the code violates the grammar or rules of a programming language

Consider the following syntax error:
```python
if a <> b:
	print("a is equal to b")
```

Although `<>` may be a valid operator in other languages, since it does not exist in python, it does constitute a syntax error.

Therefore the proper syntax should be as follows:
```python
if a != b:
	print("a is equal to b")
```

## 6.1.2 Static Semantic Errors

> [!info] Static Semantic Errors
> Errors that occurs when code is syntactically correct but has an incorrect use of program statements

Consider the following static semantic error:
``` python
s = "my string"
s = s - 2
```

This code will throw a `TypeError` because the variable is of the wrong type when the `-` operator is used.

Other static semantic errors commonly encountered in python include:

| Error           | Cause                                                                |
| --------------- | -------------------------------------------------------------------- |
| `NameError`     | Unknown variable/object is used                                      |
| `IndexError`    | Index provided is outside the range of the list                      |
| `ValueError`    | A value with correct type but wrong format is passed into a function |
| `ArributeError` | Attribute does not exist                                             | 

## 6.1.3 Logic Errors

> [!info] Logic Errors
> Errors that occur when a code is able to run but it produces a unintended result

These errors are the hardest to debug as there is no indication of the problem output by the compiler/interpreter

Consider the following logic error:
```python
from math import pi
radius = 10
areaOfCircle = pi * (radius ** 3)
```

Since an incorrect formula is used, the result of areaOfCircle is false. However, this will not be picked up by the compiler/interpreter.

logic errors are typically **run-time errors** as they occur while the program is already running

## 6.1.4 Arithmetic Errors

> [!info] Arithmetic Errors
> Errors that occur when an illegal mathematical expression is used

These errors commonly occur as run-time errors and are not picked up by the compiler/interpreter

Examples include:
- **Division by zero**
- **Overflow error** → a value that is too large to be represented by the number of bits allocated for it, leading to negative values.
- **Underflow error** → A value that is too small to be represented by the number of bits allocated for it, leading to a value of zero.
- **Approximation error** → Errors in the preciseness of decimal values due to the limitations of floating point arithmetic

# 6.2 Error Handling

Error handling is important in python to handle exceptions that are raised by a procedure.

This can be achieved by using `try`/`except` statements:
```python
try:
	# code that might raise an exception
except:
	# code that runs if an exception is raised
else: #optional
	# code that runs if an exception is not raised
finally: #optional
	# always executes afterwards
```

A specific error can also be checked for using this syntax:
```python
except ValueError:
	# code goes here
```

Multiple except statement can also be used to catch several different errors:
```python
except ZeroDivisionError:
	print("Error: Divided by Zero")
except (ValueError, TypeError):
	print("Error: Value or Type Error occured")
```

The full list of error classes can be viewed by running this statement:
```python
*Error?
```

# 6.3 Program Testing

Testing can be used to identify **logic** and **arithmetic errors** and some **static semantic errors**

Test cases are example values that are passed into the program to determine whether it is working

There are 3 types of test cases:
- Normal Test Cases
- Boundary Test Cases
- Abnormal Test Cases

## 6.3.1 Normal Test Cases

>[!info] Normal Test Cases
> Data that is normally input into the program.

In such cases, the program should accept the input and process it and output a result.

## 6.3.2 Boundary Test Cases

> [!info] Boundary Test Cases
> Values that are at the absolute limit of the input of the program.

They are a type of boundary test case that are extreme values to make sure that all normal values are accepted and processed correctly.

For example in a program requires a score from 0-100, a boundary test case would be the value 0 or 100.

## 6.3.3 Abnormal Test Cases

> [!info] Abnormal Test Cases
> Values that should not be accepted by the system

In this case, the program should reject the abnormal test case but not throw a run-time error.

For example, in a program that requires an integer input, an abnormal test case would be a string input.

# 6.4 Data Validation

*Not to be confused with data verification*

> [!info] Data Validation
> Process to confirm if input data conforms to required specifications in presence, existence, accuracy, length, range, format etc.

Note that it just ensures that the data has the correct type and format but does not guarantee that the data is accurate (that is data verification)

For example, Data validation is used to check if an email has an @ symbol and domain name but does not check whether the user actually owns the email.

**Data validation techniques include:**

| Technique          | Description                                                          |
| ------------------ | -------------------------------------------------------------------- |
| **Range Check**    | Check if the data is within the acceptable range/region              |
| **Format Check**   | Checks if the characters in each position follows the correct layout |
| **Length Check**   | Check if the input data has a specified number of characters         |
| **Presence Check** | Checks for empty fields                                              |
| **Check Digit**    | Checks for simple errors in an input of a series of digits           | 

# 6.5 Data verification

*Not to be confused with data validation*

> [!info] Data verification
> Process in which different types of data are checked for accuracy and inconsistencies after data migration is done.

---
*Last edited 16/08/2023 by Joshua Lim NJC*