# COMP 313 Project 2 

# 1) TODO Questions
## TestIterator.java TODO
TODO Question: Also try with a LinkedList - does it make any difference?: The output using the LinkedList is the same as with the ArrayList. There was no behavioral difference between the two.  
./gradlew Test

BUILD SUCCESSFUL in 1s
2 actionable tasks: 2 executed

TODO Question: What happens if you use list.remove(Integer.valueOf(77))?
    list.remove() is the safe way to remove the current element during iteration. 
    list.remove(Integer.valueOf(77)) would remove the first matching value of 77 directly from the list, but if it is used while iterating it may cause an exception since iterators don't like sudden changes to the list while its running. It can cause problems and unpredictable behvior. 


## TestList.java TODO

TODO Question: Also try with a LinkedList - does it make any difference?: I received the same output for both, showing no difference in behavior. 
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

	SIZE 10 (REPS: 1000000 1-6, 500000 for 7-8, 100000 for 9-10, 10000000 11-12)
								  #1   #2   #3   #4   #5   #6 	 #7    #8    #9    #10    #11     #12
        testArrayListAddRemove:  23ms 22ms 24ms 23ms 21ms 21ms  14ms  14ms   7ms   7ms   161ms   274ms
        testLinkedListAddRemove: 27ms 23ms 20ms 24ms 18ms 18ms  14ms  17ms   8ms   6ms   105ms   175ms
		testArrayListAccess:     11ms 11ms 10ms 13ms 9ms  9ms    9ms  11ms   7ms   6ms    25ms    65ms
        testLinkedListAccess:    12ms 8ms  8ms  11ms 9ms  9ms    7ms   8ms   7ms   3ms    31ms   102ms
        Total:                   73ms 64ms 62ms 71ms 57ms 57ms  44ms  50ms  29ms  22ms   322ms   616ms

For SIZE 10, I noticed that ArrayList and LinkedList performed almost the same, because the total runtime stayed between 57ms and 73ms for REPS = 1,000,000 (#1–#6). 
When I increased REPS to 10,000,000 (#11–#12), the total runtime jumped up to 322ms and 616ms, but overall both list types still remained relatively fast.

	SIZE 100 (REPS: 1000000--for 1-5 test, 500000 for 6-8, 100000 for 9-10, 10000000 11-12)
								  #1   #2   #3   #4   #5   #6 	#7    #8   #9   #10    #11    #12
        testArrayListAddRemove:  38ms 35ms 30ms 34ms 39ms  7ms 19ms  25ms  8ms  10ms  258ms  246ms
        testLinkedListAddRemove: 21ms 24ms 21ms 22ms 34ms  8ms 18ms  14ms  6ms  8ms    90ms   87ms
		testArrayListAccess:     9ms  11ms 10ms 11ms 34ms  6ms 8ms    9ms  6ms  8ms    25ms   25ms
        testLinkedListAccess:    23ms 27ms 20ms 28ms 30ms  8ms 15ms  14ms  6ms  12ms  149ms  147ms
        Total:                   91ms 97ms 81ms 95ms 137ms 29ms 60ms 62ms 26ms  38ms  522ms  505ms

For SIZE 100, I noticed LinkedListAddRemove was faster than ArrayListAddRemove (ex: 21 vs 38 on Test #1). However, ArrayListAccess was always faster than LinkedListAccess (ex: 9ms vs 23ms on #1). 
When I raised REPS to 10,000,000, ArrayListAddRemove jumped to 258/246ms, while LinkedListAddRemove stayed lower at 90/87ms, and LinkedListAccess increased to 149ms/147ms while ArrayListAccess stayed at 25ms.

	SIZE 1000 (REPS: 1000000--for 1-4 test, 500000 for 5-7, 100000 for 8-12, 10000000 13-14)
								  #1    #2    #3    #4     #5     #6     #7     #8   #9  #10  #11  #12        #13            #14
        testArrayListAddRemove:  170ms 191ms 162ms 191ms   83ms   86ms   83ms  88ms 22ms 21ms 20ms 20ms    1sec 643ms    1sec 566ms
        testLinkedListAddRemove:  32ms  23ms  26ms  22ms   12ms   26ms   18ms  22ms 8ms 10ms  7ms  6ms          100ms        143 ms
		testArrayListAccess:       9ms  14ms  12ms  16ms   10ms   13ms   10ms  12ms 7ms 6ms   6ms  6ms           21ms          34ms
        testLinkedListAccess:    365ms 342ms 355ms 352ms  175ms  193ms  177ms 184ms 48ms 43ms 45ms 42ms    3sec 632ms    3sec 608ms
        Total:                   576ms 570ms 555ms 581ms  281ms  318ms  288ms 306ms 85ms 80ms 78ms 74ms    5sec 396ms    5sec 351ms

For SIZE 1000, I observed that LinkedListAddRemove was much faster than ArrayListAddRemove (ex: 32 vs 170ms on test #1). However, ArrayListAccess stayed consistently faster than LinkedListAccess (9ms vs 365ms #1).
When I increased REPS to 10,000,000, the differences became noticeable. ArrayListAddRemove increased heavily to 1sec 643ms while LinkedListAddRemove stayed much lower at 100ms.
At the same time, LinkedListAccess jumped massively to 3sec 632ms while ArrayListAccess remained very low at only 21ms and 34ms, showing that LinkedList becomes extremely slow for access as size grows.

	SIZE 10000 (REPS: 1000000--for 1-3 test, 500000 for 4-5, 100000 for 6-8, 10000000 9-10)
								  #1           #2            #3           #4           #5         #6 	  #7      #8        #9            #10
        testArrayListAddRemove:1sec 703ms   1sec 630ms   1sec 788ms        888ms        817ms   175ms   166ms   174ms  17sec 111ms   17sec 322ms
        testLinkedListAddRemove:     30ms         24ms         23ms         20ms         19ms     8ms     7ms     7ms         90ms          95ms
		testArrayListAccess:         15ms         18ms         12ms         10ms         11ms     9ms     8ms    10ms         22ms          23ms
        testLinkedListAccess:  5sec 120ms   4sec 739ms   4sec 778ms   2sec 560ms   2sec 369ms   479ms   481ms   481ms  48sec 397ms   47sec 201ms
        Total:                 6sec 868ms   6sec 411ms   6sec 601ms   3sec 478ms   3sec 216ms   671ms   662ms   672ms    1min 6sec     1min 5sec

For SIZE 10000, I observed that LinkedListAddRemove was drastically faster than ArrayListAddRemove (ex: 30ms vs 1sec 703ms on test #1). However, I also saw that ArrayListAccess stayed consistently faster than LinkedListAccess (15ms vs 5sec 120ms on test #1).
When I increased REPS to 10,000,000, the performance gap became extreme, because ArrayListAddRemove jumped massively to 17sec 111ms while LinkedListAddRemove stayed very low at only 90ms and 95ms.
At the same time, LinkedListAccess increased to 48sec 397ms and 47sec 201ms, while ArrayListAccess remained extremely low at only 22ms and 23ms, showing that LinkedList becomes incredibly inefficient for access as the size grows.

	listAccess - which type of List is better to use, and why?

		When it comes to listAccess, ArrayLists are better to use, because my tests showed that regardless of size and the increase/decrease of REPS, ArrayListAccess was always faster than LinkedListAcess. 
        For example, in SIZE 10000 with REPS 10000000, ArrayListAccess was at 22ms while LinkedListAcess jumped to 48sec 397ms. 
        This makes sense because an ArrayList can access elements directly by index, which stays fast as the list grows, while a Linked List's has to traverse nodes via pointers, becoming slower as the size increases.  

	listAddRemove - which type of List is better to use, and why?

		When it comes to listAddRemove, LinkedLists are better to use, because my tests showed that testLinkedListAddRemove was consistently faster than testArrayListAddRemove, especially as the list size increased.
        For example, in SIZE 10000 with REPS 10000000, ArrayListAddRemove took 17 sec 111ms, while LinkedListAddRemove stayed under 100ms at 90ms. 
        This makes sense because adding or removing elements at the beginning of an ArrayList requires shifting all remaining elements, while a LinkedList only needs to update pointers, allowing add and remove operations to stay efficient even as the list grows.

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

