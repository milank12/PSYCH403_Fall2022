This is my set of answers to Assignment 1:

Print exercises:
1) See "yourname.py" file
2) No, no variables show up in the variable explorer.

Operation Exercises:
1) No, both operations output a value of 2.5
2) The modulo operator calculates the remainder after dividing two values (25%6 = 1).
3) The ** operator applies an exponent (3**2 = 9), the // operator divides and rounds down to the nearest integer (85/4 = 21).
4) Yes, python follows order of operations (12/6*2+3 = 7).

Variable Exercises:
2) Yes, I now have five seperate string variables for each letter.
3) Python does not seem to have an isse with two different variables with the sane value.
5) No, changing the value of leterX did not change the value of letter1.
6) After making letterX = letter1, changing the value of letter1 did effect the output. This means that variables can be reassigned to other variables and follow those variables rules.

Boolean exercises:
1) 1 and 1.0 are equivalent because python treats these as operations and they give the same value. However, "1" and "1.0" are not equivelent because they are treated as text and don't have the same characters.
2) Yes, 5 and (3+2) are equivalent.
3) 1. [1 == 1.0] or ["1" == "1.0"] and [5 == (3+2)]
   2. [1 == 1.0] or ["1" == "1.0"] or [5 == (3+2)]
   3. [1 == 1.0] and not ["1" == "1.0"] or [5 == (3+2)]
   4. [1 == 1.0] and ["1" == "1.0"] and [5 == (3+2)]
   5. [1 == 1.0] or ["1" == "1.0"] and [5 == (3+2)]
   
   
List exercises
1) oddlist = list(range(0,11)). Yes, oddlist became a list type variable with a size of 11 (0,11)
2) No errors when printing oddlist.
3) Python says the list is 11 numbers long.
4) Python says the variable is list type.
5) intlist = list(range(0,101)
6) Yes, python lists all 100 integers.

Dictionary exercises
1) myname = "Milan"
myage = 22.0
yearofstudy = 5
favourite_foods = ["tacos", "pizza", "ramen"]

about_me = {'name':myname, 'age':myage, 'study':yearofstudy, 'foods':favourite_foods}

2) about_me is a dictionary type variable.
3) The length of the dictionary is 4 - so python checks the amount of variables contained in the dictionary to define the length.

Array Exercises:
1)import numpy as np
mixnumpy = np.array([1,2.0,3,4.0,5,6.0])
print(mixnumpy)

In the console and variable explorer we can see that the array has become an array of floats.

2)import numpy as np
mixtypes = np.array([1, 2, 3.0, 4.0, "Name", "Age"])
print(mixtypes)

python has converted the array to an array of strings, 

3) import numpy as np
oddarray = np.linspace(1, 99, 50)
print(oddarray)

4)import numpy as np
logarray = np.logspace(0, 0.69897000433, 16)
print(logarray)

   
