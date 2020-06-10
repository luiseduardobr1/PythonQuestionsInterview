# Python Questions Interview

**1. What is the difference between ```nonlocal``` and ```global``` variable ?**
<details>
  <summary>Answer</summary>
  
Global statement permits modification of global variable in local scope and nonlocal statement permits modification of enclosing scope variable in local scope. The nonlocal statement does to enclosing scope variable what global statement does to the global variable. The nonlocal is a counterpat of the global statement. Example:
  
  ```Python
def scope_test():
    def do_local():
        spam = "local spam"

    def do_nonlocal():
        nonlocal spam
        spam = "nonlocal spam"

    def do_global():
        global spam
        spam = "global spam"

    spam = "test spam"
    do_local()
    print("After local assignment:", spam)
    do_nonlocal()
    print("After nonlocal assignment:", spam)
    do_global()
    print("After global assignment:", spam)

scope_test()
print("In global scope:", spam)
  ```

Output:
```
After local assignment: test spam
After nonlocal assignment: nonlocal spam
After global assignment: nonlocal spam
In global scope: global spam
```
Sources: [Python3 Docs](https://docs.python.org/3/tutorial/classes.html) and [CandCplusplus](http://candcplusplus.com/python-difference-between-global-statement-and-nonlocal-statement)
</details>

**2. What is the difference between ```immutable``` and ```mutable``` objects ?**
<details>
  <summary>Answer</summary>
  
  Since everything in Python is an Object, every variable holds an object instance. When an object is initiated, it is assigned a unique object id. Its type is defined at runtime and once set can never change, however its state can be changed if it is mutable. Simple put, a mutable object can be changed after it is created, and an immutable object can’t.
  
  ```
  Immutable Objects: int, float, bool, string, unicode, tuple, bytes, complex

  Mutable Objects: list, dict, set, class (generally), array
  ```

  Conclusions:

* Mutable and immutable objects are handled differently in python. Immutable objects are quicker to access and are expensive to change because it involves the creation of a copy. Whereas mutable objects are easy to change.
* Use of mutable objects is recommended when there is a need to change the size or content of the object.
* Exception : However, there is an exception in immutability as well. We know that tuple in python is immutable. But the tuple consists of a sequence of names with unchangeable bindings to objects.
Consider a tuple
 ```tup = ([3, 4, 5], 'myname')```.
The tuple consists of a string and a list. Strings are immutable so we can’t change its value. But the contents of the list can change. The tuple itself isn’t mutable but contain items that are mutable.

Sources: [Mutable vs Immutable Objects in Python - Megha Mohan](https://medium.com/@meghamohan/mutable-and-immutable-side-of-python-c2145cf72747) and [Geeks for Geeks](https://www.geeksforgeeks.org/mutable-vs-immutable-objects-in-python/)
  
</details>

**3. What is the difference between ```is``` and ```==``` operators ?**
<details>
  <summary>Answer</summary>
  
The ```==``` operator compares the values of two objects and returns **True** if the two objects have the same value. The ```is``` operator returns **True** only if the two objects being compared are the same object.

You normally use the ```==``` operator except in a few special cases, one of which is where you are specifically comparing a value against ```None```. In that case you do ```if result is None:```.

Example:
  ```Python
x = [1,2,3]
y = [1,2,3]
print(x == y)
print(x is y)
print(id(x))
print(id(y))
  ```
Output:
```
True
False
29970824
29971336
```
Source: [r/learnpython](https://www.reddit.com/r/learnpython/comments/ee3pwk/what_is_the_difference_between_is_operators_in/)
  
</details>

**4. How to copy the values (not reference) of a list and a dictionary ?**
<details>
  <summary>Answer</summary>
  
  * Copy a list to a new variable: 
  ```Python
a = b[:]
  ```
OBS: Pass by reference: ```a = b```, if you change the values of ```a```, it will change ```b``` too, because it's the same object. 

  * Copy a dictionary to a new variable: 
  ```Python
dict2 = dict(dict1)

or

dict2 = dict1.copy()
  ```

Other solution:
```Python
import copy

list2 = copy.deepcopy(list1)
dict2 = copy.deepcopy(dict1)
```
  
</details>

**5. Enumerate the differences between a list, dictionary and tuple.**
<details>
  <summary>Answer</summary>
  
| Category         | List                                                          | Dictionary                                | Tuple                                         |
|------------------|---------------------------------------------------------------|-------------------------------------------|-----------------------------------------------|
| Type             | mutable/non-hashable                                          | mutable/non-hashable                      | immutable/hashable                            |
| Elements context | Generally, same context                                       | Same or different                         | Usually, different context                    |
| Elements index   | Ordered, access by position                                   | Not-ordered*, access by "keys"            | Ordered, fixed position                       |
| Particularity    | List can't be a dictionary's key, but it can be its "value"  | There aren't duplicate keys               | It can replace the list as dictionary's "key" |
| Particularity    | -                                                             | There aren't restrictions of its "values" | -                                             |
  
\* After Python3.7, the position is preserved. 
</details>




