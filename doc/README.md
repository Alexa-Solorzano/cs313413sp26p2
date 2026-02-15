# COMP 313 Project 2 

# 1) TODO Questions
## TestIterator.java TODO
TODO Question: Also try with a LinkedList - does it make any difference?: The output using the LinkedList is the same as with the ArrayList.There was no behavioral difference between the two.  
./gradlew Test

BUILD SUCCESSFUL in 1s
2 actionable tasks: 2 executed

TODO Question: What happens if you use list.remove(Integer.valueOf(77))?
    list.remove() is the safe way to remove the current element during iteration. 
    list.remove(Integer.valueOf(77)) would remove the first matching value of 77 directly from the list during iteration. 


## TestList.java TODO

TODO Question: Also try with a LinkedList - does it make any difference?: I received the same output for both, showing no difference in initialization. 
./gradlew Test

BUILD SUCCESSFUL in 1s
2 actionable tasks: 2 executed

TODO Question: What does this method (list.remove())do?
The real way to frame list.remove() is by knowing whether what is being removed for certain is the element at the index
specified by the () OR the actual value inside the (). EX: list.remove(3) could be index 3 (4th item) or the position were the value is 3. 
Here, (list.remove(5)) removes the element at index 5 (since Java uses a 0-based indexed count, 5 would be the 6th item) and not the actual integer 5. 

TODO Question: What does this one do? (list.remove(Integer.valueOf(5));)
    The difference here is that .remove() has the added value of Integer.valueOf(5) which would specify that what should be removed is the actual value of 5 (integer), not the index. 

## TestPerformance.java TODO

What are the results?: TODO run test and record running times for SIZE = 10, 100, 1000, 10000, ...

State how many times the tests were executed for each SIZE (10, 100, 1000 and 10000)
to get the running time in milliseconds and how the test running times were recorded.
These are examples of SIZEs you might choose, you can choose others if you wish.

	SIZE 10
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  val1 val2 val3 val4 val5 val6  ... (fill these in in ms)
        testLinkedListAddRemove: val1 val2 val3 val4 val5 val6
		testArrayListAccess:     val1 val2 val3 val4 val5 val6
        testLinkedListAccess:    val1 val2 val3 val4 val5 val6

	SIZE 100
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  val1 val2 val3 val4 val5 val6  ... (fill these in in ms)
        testLinkedListAddRemove: val1 val2 val3 val4 val5 val6
		testArrayListAccess:     val1 val2 val3 val4 val5 val6
        testLinkedListAccess:    val1 val2 val3 val4 val5 val6

	SIZE 1000
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  val1 val2 val3 val4 val5 val6  ... (fill these in in ms)
        testLinkedListAddRemove: val1 val2 val3 val4 val5 val6
		testArrayListAccess:     val1 val2 val3 val4 val5 val6
        testLinkedListAccess:    val1 val2 val3 val4 val5 val6

	SIZE 10000
								  #1   #2   #3   #4   #5   #6 	... (as many tests as you ran)
        testArrayListAddRemove:  val1 val2 val3 val4 val5 val6  ... (fill these in in ms)
        testLinkedListAddRemove: val1 val2 val3 val4 val5 val6
		testArrayListAccess:     val1 val2 val3 val4 val5 val6
        testLinkedListAccess:    val1 val2 val3 val4 val5 val6

	listAccess - which type of List is better to use, and why?

		Your answer here.

	listAddRemove - which type of List is better to use, and why?

		Your answer here.

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

# ./gradlew Test Results AFTER I:
## * TestList.java:
** Filled in expected values for: **
- testSizeNonEmpty 
- testAddMultiple 
- testAddMultiple2 
- testRemoveObject 

** Assert argument before + after adding 77 **
- testContains

** Added one argument a line **
- testAddAll
- testRemoveAll

## * TestIterator.java:
** Filled expected values for iterator order **
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

# ./gradlew Test Results AFTER I:
## Fixed the rest of the AssertionErrors 
BUILD SUCCESSFUL in 1s
2 actionable tasks: 2 executed

## * TestList.java:
** Used containsAll() with List.of() to test multiple values at once **
- testContainsAll()

** Added argument using retainAll() to filter list down to only elements of 77 **
- testRetainAll()

** Used list.set() to replace all 77 values with 99 **
-testSet

** Fixed subList() to return specific middle section of list **
- testSubList

## * TestIterator.java:
** Used assertEquals & List.of() to confirm which values of the list remained after removing 77s **
- testRemove

** Used an iterator with a while loop to compute sum & count (n) to accurately calculate average **
- testAverageValues 

