# Reading and Writing Files in Python 

## Open and close files 
To open a file in python first u need to know its path. 
after that u can just invoke the built in fucntion open 
 ```
  file = open('file.extention')

 ```
 
 > Its your resposiblity to close a file after you open it when the application or script ends , at some point it will close automaticlly but you cant really know when that will happen and that could consume too much resources , it is also a best practice in pyton to make sure ur code closes the file after being done with it

so to close a file (we opened one using the variable file up there)

  ```
   file.close()

  ```
another way to close a file is using the with statment 
 ``` 
  with open('file.extention') as file:
     # some file processing 
 ```
The with statment will close the file automaticlly when the code block ends 

## Read and Write opened files

### Reading a file 
There is plenty of ways to read an opened file 
 
Method	What It Does
* .read(size=-1)	This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.

* .readline(size=-1)	This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.

* .readlines()	This reads the remaining lines from the file object and returns them as a list.
(copied from https://realpython.com/read-write-files-python/#opening-and-closing-a-file-in-python)

to read the whole file using the .read u can do this

 ```
 with open('file.extention','r') as file: 
     print(file.read())

   #reading 5 bytes of each line 
   print(file.readline(5))
   #reading the file as list using the readlines
   f=open('text.txt')
   f.readlines()

 ```

### Writing in a file 
to write in a file u can use 
* .write(string)	This writes the string to the file.

* .writelines(seq)	This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to you to add the appropriate line ending(s).


examples :

 ```
 with open('dog_breeds.txt', 'r') as reader:
    dog_breeds = reader.readlines()

 with open('dog_breeds_reversed.txt', 'w') as writer:
    for breed in reversed(dog_breeds):
        writer.write(breed)
 ```
(copied from https://realpython.com/read-write-files-python/#opening-and-closing-a-file-in-python)

# Python Exceptions

Expections happen when the python code is syntactically correct but u run into an error (the last line of the error tells you what type of exception it is)

## Raising an exception 
We can use raise to throw an exception if a condition occurs using rais like this 
 ```
  x = 10
  if x > 5 :
   raise Exception(f"x should not be be bigger than 5,the value of x was {x}")
 ```
when this code run u will get an exception error with the message u put 

## The AssertionError Exception
inistead of waiting for the application to crash midway u can use assertoin 

 ```
  import sys
  assert ('linux' in sys.platform), "This code runs on Linux only."

 ```
 if you run that code on a machin that is using the Linux system it will pass , other than that the outcome of the assertion would be false and u will revice the exception msg " this code runs on linux only"

 ## The try and except Block: Handling Exceptions
 The try and except block in Python is used to catch and handle exceptions. Python executes code following the try statement as a “normal” part of the program. The code that follows the except statement is the program’s response to any exceptions in the preceding try clause.

 ```
  def linux_interaction():
    assert ('linux' in sys.platform), "Function can only run on Linux systems."
    print('Doing something.')
 
  try:
    linux_interaction()
  except AssertionError as error:
    print(error)
    print('The linux_interaction() function was not executed')

 ```

If you on a windows system and try to run the previous code u will recive 
 > Function can only run on Linux systems.
 >The linux_interaction() function was not executed
First message is the assertion error telling u that the fucntion can only run on linux and the 2nd one tells u what function didnt excute 


## The else Clause
In Python, using the else statement, you can instruct a program to execute a certain block of code only in the absence of exceptions.

 ```
  try:
    linux_interaction()
 except AssertionError as error:
    print(error)
 else:
    print('Executing the else clause.')
 ```
if u run this on linux it will print 'Executing the else clause' because it didnt run into exception it went to the else clause 

## finally
 finally enables you to execute sections of code that should always run, with or without any previously encountered exceptions.
 
 ```
   try:
       linux_interaction()
   except AssertionError as error:
        print(error)
   else:
       try:
         with open('file.log') as file:
              read_data = file.read()
        except FileNotFoundError as fnf_error:
           print(fnf_error)
   finally:
       print('Cleaning up, irrespective of any exceptions.')

 ```
Everything in the finally clause will be executed it dosnt matter if u run into an exception 
