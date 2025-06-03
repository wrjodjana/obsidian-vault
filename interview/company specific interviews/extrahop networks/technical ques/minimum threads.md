>[!question]
> You are given a list of characters and a target word that contains no duplicate characters.
> One or more threads will consume characters from the array to form the target word, following certain rules:
> 1. A thread must consume characters in the order that they appear in the target word
> 2. All characters from the list must be consumed in order. If a thread cannot consume the next
> character in the array, it must wait until the character has been consumed by a different thread
> 3. Each character from the list can only be consumed by one thread
> 4. Each thread can work on only one instance of the target word at a time. However, once a thread has consumed the final character of the target word, it may start over and attempt to form another instance of the target word

