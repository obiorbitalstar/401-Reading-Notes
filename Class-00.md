# BIG O notaion 

In simple terms, big o can be explained as to how time scales concerning some input variables
Let's use a small story to explain some of it.

In 2009 there was this African company that had a slow internet connection, So they wanted to make a fun test they put the data they wanted to move in a USB drive and tied it to a pigeon, It was a race between a pigeon and the internet, ofc the pigeon won or this wouldn't have been covered by the news, I think this comparison is a little unrealistic or unfair because the amount of data doesn't matter for the pigeon, It just has to cross the same distance regardless of the size of data put in the USB while for the internet the size of data matters, So how can we change this story to big o? We are gonna cut it into examples with explanations

## O(1)

O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set. So O(1) is the pigeon in out story, regardless of the size of data put in the USB it will need the same amount of time to go from point A to point Bso o(1) deals with constant time or constant inputs


## O(N)

O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set. O(N) is the internet in our story, The amount of data u want to send effect the time needed to upload it, so O(N) deals with linear time and is affected by the input


## O(N^2)
O(N^2) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. I don't know how to apply this on our pigeon story so let's try a different one. Let’s say you’re making dinner for your family. O is the process of following a recipe, and n is the number of times you follow a recipe O(N^2) would be you making individual dishes redundantly for every person. You follow all recipes for each person in your family (recipe times the number of people squared).

 