# Hash table 

## Terminology:

* Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.

* Buckets - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.

* Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.
Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.

## Why do we use them?
Hold unique values
Dictionary
Library

## What Are they
Hashtables are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value.

## Structure

### Creating a Hash

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

Example: 

    ``` 
    Key = "Cat"
    Value = "Josie"

    67 + 97 + 116 = 280

    280 * 599 = 69648

    69648 % 1024 = 16

    Key gets placed in index of 16. 

    ```

## Notes 
 Hash maps do this to store values:
 * accept a key
 * calculate the hash of the key
 * use modulus to convert the hash into an array index
 * store the key with the value by appending both to the end of a linked  list

 Hash maps do this to read value:
 * accept a key
 * calculate the hash of the key
 * use modulus to convert the hash into an array index
 * use the array index to access the short LinkedList representing a  bucket
 * search through the bucket looking for a node with a key/value pair that matches the key you were given  


## Internal Methods
1. Add()
When adding a new key/value pair to a hashtable:

send the key to the GetHash method.
Once you determine the index of where it should be placed, go to that index
Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
If something does exist, add the new key/value pair to the data structure within that bucket.
2. Find()
The Find takes in a key, gets the Hash, and goes to the index location specified. Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists and return the value.

3. Contains()
The Contains method will accept a key, and return a bool on if that key exists inside the hashtable. The best way to do this is to have the contains call the GetHash and check the hashtable if the key exists in the table given the index returned.

4. GetHash()
The GetHash will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.



