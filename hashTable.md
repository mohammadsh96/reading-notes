# Hashtables
[back to main](./README.md)
- What is a Hashtable?
- Terminology:

- `Hash` - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.
`Buckets` - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

- Why do we use them?
`Hold unique values`
`Dictionary`
`Library`
- What Are they?
`Hashtables` are a `data structure` that utilize `key value pairs`. This means every Node or Bucket has both a key, and a value.

- The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value. This is done through what we call a hash. A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

Since we are able to hash our key and determine the exact location where our value is stored, we can do a lookup in an O(1) time complexity. This is ideal when quick lookups are required.

Example
Let’s say we have data of Seattle neighborhood names and their corresponding zip codes.
```js
["Greenwood:98103", "Downtown:98101", "Alki Beach:98116", "Bainbridge Island:98110", ...]
```
Now, we want to be able to search through the data to look up a neighborhood and obtain it’s zip code. We could do this using a for loop that looks through each piece of data one by one until it finds the neighborhood name, then returns the zip code there. This would be an O(N) read operation because it requires searching through each piece of data to find the one piece we want.

Arrays actually have fast access. If we know the index of the information we want we can access that information in O(1) time. The reason why searching for a piece of data in a collection is O(N) isn’t because the array is slow, it’s just that we have to look through all N things in the collection.

Hash maps take advantage of an array’s O(1) read access. Instead of adding elements to an array from beginning to end, a hash map uses a “hash function” to place each item at a precise index location, based off it’s key.

Basically, the hash function takes a key and returns an integer. We use the integer to determine where the key/value pair should be placed in the array. The hash code is calculated in constant time and writing to an array at one index is O(1) so the hash map has O(1) access.

The hash code is used again to read something from the hash map. Take the key, run it through the hash code to get a number, use that number to index the array. Calculating the hash code and reading an array at that index is all constant time to the hash map has O(1) read access!

Structure
Hashing
Basically, a hash code turns a key into an integer. It’s very important that hash codes are deterministic: their output is determined only by their input. Hash codes should never have randomness to them. The same key should always produce the same hash code.

## `Creating a Hash`
- A hashtable traditionally is created from an array. I always like the size 1024. this is important for index placement. After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a simplistic hashing algorithm:

Add or multiply all the ASCII values together.
Multiply it by a prime number such as 599.
Use modulo to get the remainder of the result, when divided by the total size of the array.

Insert into the array at that index.
Example:
```js
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16
```
Key gets placed in index of 16. 

We now know that our key Cat maps to index 16 of the array. We can view into this index and find “Josie”, our value quickly.

NOTE: Production systems will have much more robust hashing algorithms that ensure even distribution of values across all buckets and avoid unnecessary collisions.
 ## Internal Methods

`Add()`
When adding a new key/value pair to a hashtable:

send the key to the GetHash method.
Once you determine the index of where it should be placed, go to that index
Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
If something does exist, add the new key/value pair to the data structure within that bucket.

`Find()`
The Find takes in a key, gets the Hash, and goes to the index location specified. Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists and return the value.


`Contains()`
The Contains method will accept a key, and return a bool on if that key exists inside the hashtable. The best way to do this is to have the contains call the GetHash and check the hashtable if the key exists in the table given the index returned.


``GetHash()``
The GetHash will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.

### recourses : 
- https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html
- https://www.youtube.com/watch?v=MfhjkfocRR0
- https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/
- https://en.wikipedia.org/wiki/Hash_table 