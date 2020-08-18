# Classes and Objects in python
Objects are an encapsulation of variables and functions into a single entity. objects get thier variables and functions from classes 
an example of a class would be something like this :
 ```
 class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")
 ```
to assign this class to an object write:
 ```
  myobject= MyClass()
 ```
to acess variables in the object 
 ```
  myobject.variable 
 ```
you can link many object to the same class having the same variables and fucntions, each object will be an
independent copy 

# Thinking recursively in python 
>If the current problem represents a simple case, solve it. If not, divide it into subproblems and apply the same strategy to them.

in python a recursive function is a function that calls it self and repeat its behaviour until some conditoins are met to return a result 
all recursive functions share the same structure , a base case and a recursive case 

Recursive function for calculating n! implemented in Python:
 ``` 
 def factorial_recursive(n):
    # Base case: 1! = 1
    if n == 1:
        return 1

    # Recursive case: n! = n * (n-1)!
    else:
        return n * factorial_recursive(n-1)
 ```

 # Python Testing with pytest: Fixtures and Coverage

 ## Fixtures
When writing a test ur usually not going to write just a few test , you will try to test every case 
and some times these tests can have similar characteristics that pytest handles using parametrized tests.

But in other cases, things are a bit more complex. You'll want to have some objects available to all of your tests. Those objects might contain data you want to share across tests, or they might involve the network or filesystem. These are often known as "fixtures" in the testing world, and they take a variety of different forms.

In pytest, you define fixtures using a combination of the pytest.fixture decorator, along with a function definition. For example, say you have a file that returns a list of lines from a file, in which each line is reversed
 ``` 
  def reverse_lines(f):
   return [one_line.rstrip()[::-1] + '\n'
           for one_line in f]
 ```
 If you're going to test this function, you'll need to pass it a file-like object, you can create a fixture that'll provide your test with the appropriate object at the right time.
 
 here how it looks in pytest: 
  ```
  @pytest.fixture
   def simple_file():
   return StringIO('\n'.join(['abc', 'def', 'ghi', 'jkl']))

  ```

this was summarized from this article ( https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)

