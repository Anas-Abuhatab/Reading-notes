# Hash Tables

### Intro to Hash Tables
- Hash: Result of an algorithm taking a string and then converting it into a value that could be usef for a purpose. In context of hashtables, it is used to determine the index of the array. 
- Buckets: The contents of each index in the array of the hashtable. Basically, each index is a bucket.
- Collisions: When multiple keys get hashed to the same location (index) in the hashtable. 
- Uses:
  1. Hold unique values
  2. Dictionary
  3. Library
- Hashtables are a data structure that utilize key value pairs.
- Retrieving value in hashtable is O(1) time complexity.
- Example:
```
["Greenwood:98103", "Downtown:98101", "Alki Beach:98116", "Bainbridge Island:98110", ...]
```
- Hash maps take advantage of an array's O(1) read access. 
- hash map uses a “hash function” to place each item at a precise index location, based off it’s key.
- Hash function takes a key and returns an integer.
- hash code is calculated in constant time and writing to an array at one index is O(1) so the hash map has O(1) access.
- Hash codes should NOT have randomness to them!
- Example:
```
Key = "Cat"
Value = "Josie"
# Add or multiply all the ASCII values together.
67 + 97 + 116 = 280
# Multiply it by a prime number such as 599.
280 * 599 = 69648
# Use modulo to get the remainder of the result, when divided by the total size of the array.
69648 % 1024 = 16

Key gets placed in index of 16. 
```
- initialize a LinkedList in each index (bucket) to allow for different keys to hash to that same bucket.  
- store the entire key/value pair in the bucket, not just the value.
- Example of collision: 
```
hashMap.Add("Pioneer Square", 98104);
hashMap.Add("Alki Beach", 98116);
Bucket 92: [{Pioneer Square: 98104} --> {Alki Beach: 98116}]
```
- Process for hashmaps to store values:
  1. accept a key
  2. calculate the hash of the key
  3. use modulus to convert the hash into an array index
  4. store the key with the value by appending both to the end of a linked list
- Process for hashmaps to read values:
  1. accept a key
  2. calculate the hash of the key
  3. use modulus to convert the hash into an array index
  4. use the array index to access the short LinkedList representing a bucket
  5. search through the bucket looking for a node with a key/value pair that matches the key you were given
- A hash table can start with just a few bucks but calculate it's own load factor, recognizing when it gets to full and automatically expand, adding more buckets to accomodate the data.
- Add() method: add a new key/value pair to a hashtable.
- Find() method: Takes in a key, gets the Hash, and goes to the index location. If the key exists, it will return the value.
- Contains() method: Accept a key and returns a bool on if that key exists inside the table. 
- GetHash() method: Accept a key as a string, conduct hash, and return the index of the array where they key/value pair should be placed. 

### what is a hash table?
- Key and value pairs
- Array structure
- Hash tables are typically very larger
- Hash(key) -> index (returns index)
- You can chain multiple key value pairs at the same index. 
- If collision, just chain off of that index number. 
