# COMP 313 Project 2 

# 1) TODO Questions
## TestIterator.java TODO
TODO Question: Also try with a LinkedList - does it make any difference?

TODO Question: What happens if you use list.remove(Integer.valueOf(77))?
    list.remove() is the safe way to remove the current element during iteration. 
    list.remove(Integer.valueOf(77)) would remove the first matching value of 77 directly from the list during iteration. 


## TestList.java TODO

TODO Question: Also try with a LinkedList - does it make any difference?

TODO Question: What does this method (list.remove())do?
The real way to frame list.remove() is by knowing whether what is being removed for certain is the element at the index
specified by the () OR the actual value inside the (). EX: list.remove(3) could be index 3 (4th item) or the position were the value is 3. 
Here, (list.remove(5)) removes the element at index 5 (since Java uses a 0-based indexed count, 5 would be the 6th item) and not the actual integer 5. 

TODO Question: What does this one do? (list.remove(Integer.valueOf(5));)
    The difference here is that .remove() has the added value of Integer.valueOf(5) which would specify that what should be removed is the actual value of 5 (integer), not the index. 

## TestPerformance.java TODO

What are the results?: TODO run test and record running times for SIZE = 10, 100, 1000, 10000, ...

TODO Question: What conclusions can you draw about the performance of LinkedList vs. ArrayList when

# 2) ./gradlew Test Results BEFORE any changes:
> Task :test FAILED

TestIterator > testAverageValues FAILED
java.lang.AssertionError at TestIterator.java:100

TestIterator > testRemove FAILED
java.lang.AssertionError at TestIterator.java:83
.
.
.
20 tests completed, 14 failed

FAILURE: Build failed with an exception.

# 2) ./gradlew Test Results AFTER I:
## * TestList.java:
** Filled in expected values for: **
- testSizeNonEmpty 
- testAddMultiple 
- testAddMultiple2 
- testRemoveObject 

** Assert argument before + after adding 77**
- testContains

** Added one argument a line **
- testAddAll
- testRemoveAll

## * TestIterator.java
** Filled expected values for iterator order
- testNonempty

## Majority of the failures were AssertionErrors so I focused first on filling in the expected values and iterator sequence. 
> Task :test FAILED

TestIterator > testAverageValues FAILED
java.lang.AssertionError at TestIterator.java:100

TestIterator > testRemove FAILED
java.lang.AssertionError at TestIterator.java:83

TestList > testSet FAILED
java.lang.AssertionError at TestList.java:192

TestList > testRetainAll FAILED
java.lang.AssertionError at TestList.java:174

TestList > testContainsAll FAILED
java.lang.AssertionError at TestList.java:126

TestList > testSubList FAILED
java.lang.AssertionError at TestList.java:211

20 tests completed, 6 failed

FAILURE: Build failed with an exception.