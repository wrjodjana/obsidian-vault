>[!question]
> You are given a list of characters and a target word that contains no duplicate characters.
> One or more threads will consume characters from the array to form the target word, following certain rules:
> 1. A thread must consume characters in the order that they appear in the target word
> 2. All characters from the list must be consumed in order. If a thread cannot consume the next character in the array, it must wait until the character has been consumed by a different thread
> 3. Each character from the list can only be consumed by one thread
> 4. Each thread can work on only one instance of the target word at a time. However, once a thread has consumed the final character of the target word, it may start over and attempt to form another instance of the target word
> 
> Write a function that returns the minimum number of threads required to process the list. If it is impossible to process the list due to an invalid character sequence, or if any thread is unable to construct the full word after consuming all characters in the list, return -1.

**Questions:**
- What if the input list/target word is empty? what should it return
- What does "consume characters in order" mean for the list? Does this mean we process the list from left to right and no thread can skip ahead?

**Understand:**
- Threads that need form the target word by consuming characters in order
- Each thread maintains its current position in the target word (which character it needs next)
- Characters from list must be consumed sequentially (no skipping ahead)

**Approach**
- **Brute force:** Trying like with 1 thread, 2 threads, 3 threads etc. until a configuration would work. For each number of threads simulate the process, go through character list one by one assign each character to any available thread that needs it and see if all characters get consumed and all threads completes their work. return minimum number of threads that successfully processes list, or -1
- **Optimal:**
	- We need to minimize threads by maximizing reuse - completed threads should immediately start new words rather than staying idle
	- First, when we see the first char in target word, check if any threads just finished work, if yes then reuse that immediately but if not create a new thread (ensures we are maximizing the use of the threads)
	- 
