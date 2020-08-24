# The global Statement

You already know that when you try to assign a value to a global name inside a function, you create a new local name in the function scope. To modify this behavior, you can use a global statement. With this statement, you can define a list of names that are going to be treated as global names.

The statement consists of the global keyword followed by one or more names separated by commas. You can also use multiple global statements with a name (or a list of names). All the names that you list in a global statement will be mapped to the global or module scope in which you define them.

    ``` 
    >>> counter = 0  # A global name
    >>> def update_counter():
    ...     global counter  # Declare counter as global
    ...     counter = counter + 1  # Successfully update the counter
    ...
    >>> update_counter()
    >>> counter
    1
    >>> update_counter()
    >>> counter
    2
    >>> update_counter()
    >>> counter
    3
    ```
in this new version of update_counter(), you add the statement global counter to the body of the function right before you try to change counter. With this tiny change, you’re mapping the name counter in the function scope to the same name in the global or module scope. From this point on, you can freely modify counter inside update_counter(). All the changes will reflect in the global variable.

With the statement global counter, you’re telling Python to look in the global scope for the name counter. This way, the expression counter = counter + 1 doesn’t create a new name in the function scope, but updates it in the global scope.

## Nonlocal statment 
Similarly to global names, nonlocal names can be accessed from inner functions, but not assigned or updated. If you want to modify them, then you need to use a nonlocal statement. With a nonlocal statement, you can define a list of names that are going to be treated as nonlocal.

 ```
    >>> def func():
    ...     var = 100  # A nonlocal variable
    ...     def nested():
    ...         nonlocal var  # Declare var as nonlocal
    ...         var += 100
    ...
    ...     nested()
    ...     print(var)
    ...
    >>> func()

 ```

 With the statement nonlocal var, you tell Python that you’ll be modifying var inside nested(). Then, you increment var using an augmented assignment operation. This change is reflected in the nonlocal name var, which now has a value of 200.
 Unlike global, you can’t use nonlocal outside of a nested or enclosed function. To be more precise, you can’t use a nonlocal statement in either the global scope or in a local scope.



 recorces :https://realpython.com/python-scope-legb-rule/#the-global-statement
 ps:The subjcet is clear and didnt know how to change or explain it in diffrent terms so its copied directely