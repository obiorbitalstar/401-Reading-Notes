# List Comprehensions
its a nice way to create a list, You have brackets containing expresson followed by anything which means u can put all kinds of objects inside lists
the result will be a new list from the the expression in the context of the for and if clasuss which follow it 

previously we used to populate lists like this 

 ```
    new_list = []
    for i in old_list:
    if filter(i):
        new_list.append(expressions(i))

 ```
you can do it in a cleaner better way using list comprehensions

 ``` 
 new_list = [expression(i) for i in old_list if filter(i)

 ```
so the basic syntax will be somthing like 

 ```
    [expression for item in list if condtional]

 ```
the previous code of creating a list can be broken and explained as follows:

* new_list
The new list (result).

* expression(i)
Expression is based on the variable used for each element in the old list.

* for i in old_list
The word for followed by the variable name to use, followed by the word in the
old list.

* if filter(i)
Apply a filter with an If-statement.

