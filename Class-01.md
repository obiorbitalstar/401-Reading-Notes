# Python Modules 

Modular progamming is the process of spliting a large programming task into smaller and easier to handel subtasks (divide and conquer).
it makes maintaing ,reusing ,scoping the programe easier 

There are 3 ways to define a moudle in python 
* in python itself 
* it can be written in c and loaded at runtime 
* Built in moudles 
but the content of the moudle in the 3 ways is accesed  using the same method using the import statment 

lets assume we have a file named mod.py that contains the following 
 ``` 
 s = "If Comrade Napoleon says it, it must be right."
 a = [100, 200, 300]

 def foo(arg):
    print(f'arg = {arg}')

 class Foo:
    pass
 ```
(code copied from https://realpython.com/python-modules-packages/)

now if we type 
 ```
 import mod 
 ```
When the interpreter executes the above import statement, it searches for mod.py in a list of directories assembled from the following sources:

The directory from which the input script was run or the current directory if the interpreter is being run interactively
The list of directories contained in the PYTHONPATH environment variable, if it is set. (The format for PYTHONPATH is OS-dependent but should mimic the PATH environment variable.)
An installation-dependent list of directories configured at the time Python is installed 

Thus, to ensure your module is found, you need to do one of the following:

Put mod.py in the directory where the input script is located or the current directory, if interactive
Modify the PYTHONPATH environment variable to contain the directory where mod.py is located before starting the interpreter
Or: Put mod.py in one of the directories already contained in the PYTHONPATH variable
Put mod.py in one of the installation-dependent directories, which you may or may not have write-access to, depending on the OS
(copied from the article linked above)


## The import statment 
Whats inside the module is made available using the import statment but that dose not mean you can directly use it 
so if we type 
 ``` 
  import mod 
 ```
u cant use the variables inside it directly 
 ```
 #writing somthing like this will give u an error  
 print(s)
 #to access the variable s u need to use the dot notation 
 print(mod.s)
 ```
there are other ways to use the import statment such as

 ``` 
 import <module_name>[, <module_name> ...]
 #this allows serveral moudles to be imported at the same time 
 from <module_name> import <name(s)>
 #using this form u can import individual objects
 from <module_name> import *
 #using this u import everything from a module
 ```

# Pytest 
The pytest is a framework that makes it easy write simple or complex tests for ur application 
ex: 
 ```
 # content of test_sample.py
 def inc(x):
    return x + 1
 def test_answer():
    assert inc(3) == 5
 ``` 
to test it write in the terminal 
 ``` 
 pytest
 ```
the output would be somthing like 
 ```
  =========================== test session starts ============================
platform linux -- Python 3.x.y, pytest-6.x.y, py-1.x.y, pluggy-0.x.y
cachedir: $PYTHON_PREFIX/.pytest_cache
rootdir: $REGENDOC_TMPDIR
collected 1 item

test_sample.py F                                                     [100%]

================================= FAILURES =================================
_______________________________ test_answer ________________________________

    def test_answer():
>       assert inc(3) == 5
E       assert 4 == 5
E        +  where 4 = inc(3)

test_sample.py:6: AssertionError
========================= short test summary info ==========================
FAILED test_sample.py::test_answer - assert 4 == 5
============================ 1 failed in 0.12s =============================
 ```

code and output are copied from (https://docs.pytest.org/en/latest/)


# Recursion
Recursion is the process of a fucntion calling it self and the corresponding function is called as recursive function
using recursion makes solving some problems easier 

ex :
 ```
 
 # A Python 3 program to 
 # demonstrate working of 
 # recursion 
  
 def printFun(test): 
  
    if (test < 1): 
        return
    else: 
      
        print( test, end = " ") 
        printFun(test-1) # statement 2 
        print( test, end = " ") 
        return
      
  
 test = 3
 printFun(test) 
  
 # This code is contributed by 
 # Smitha Dinesh Semwal 

 ```

When printFun(3) is called from main(), memory is allocated to printFun(3) and a local variable test is initialized to 3 and statement 1 to 4 are pushed on the stack as shown in below diagram. It first prints ‘3’. In statement 2, printFun(2) is called and memory is allocated to printFun(2) and a local variable test is initialized to 2 and statement 1 to 4 are pushed in the stack. Similarly, printFun(2) calls printFun(1) and printFun(1) calls printFun(0). printFun(0) goes to if statement and it return to printFun(1). Remaining statements of printFun(1) are executed and it returns to printFun(2) and so on

this code and its explanation are copied from (https://www.geeksforgeeks.org/recursion/)


