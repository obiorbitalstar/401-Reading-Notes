# Pythonisms 


## Dunder methods 

In Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example __init__ or __str__.

Dunder methods let you emulate the behavior of built-in types. For example, to get the length of a string you can call len('string'). But an empty class definition doesn’t support this behavior out of the box:

```
class NoLenSupport:
    pass

>>> obj = NoLenSupport()
>>> len(obj)
TypeError: "object of type 'NoLenSupport' has no len()"
```
to fix that add a len dunder method to the class 

```
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42

```

## Iterators 

python have a beautiful and clear syntax compared to other languages 

for example its for-in loop that looks like normal english syntax 

```
numbers = [1,2,3]
for n in numbers: 
    print(n)

```

but how dose it work in the background ? 
well amma answer straight up and say its using python iterator protocol: 

> Objects that support the __iter__ and __next__ dunder methods automatically work with for-in loops.


How do for-in loops work in Python?

At this point we’ve got our Repeater class that apparently supports the iterator protocol, and we just ran a for-in loop to prove it:

```
repeater = Repeater('Hello')
for item in repeater:
    print(item)

```

To dispel some of that “magic” we can expand this loop into a slightly longer code snippet that gives the same result:

```
repeater = Repeater('Hello')
iterator = repeater.__iter__()
while True:
    item = iterator.__next__()
    print(item)

```

As you can see, the for-in was just syntactic sugar for a simple while loop:

* It first prepared the repeater object for iteration by calling its __iter__ method. This returned the actual iterator object.

* After that, the loop repeatedly calls the iterator object’s __next__ method to retrieve values from it.

## Generators 

Let’s start by looking again at the Repeater example in the iterator section, It implemented a class-based iterator cycling through an infinite sequence of values.

This is what the class looked like in its second (simplified) version:

``` 
class Repeater:
    def __init__(self, value):
        self.value = value

    def __iter__(self):
        return self

    def __next__(self):
        return self.value

``` 

This is where Python’s generators enter the scene. If I rewrite this iterator class as a generator, it looks like this:

``` 
def repeater(value):
    while True:
        yield value
```
generators look like regular functions but instead of using the return statement, they use yield to pass data back to the caller.

Will this new generator implementation still work the same way as our class-based iterator did? Let’s bust out the for-in loop test to find out:

```
for x in repeater('Hi'):
    print(x)
  --> output 
  'Hi'
  'Hi' 
  'Hi'
  'Hi'
  'Hi'
   ...
```
Yep! We’re still looping through our greetings forever.





