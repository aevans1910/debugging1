# Debug Log

**Explain how you used the the techniques covered (Trace Forward, Trace Backward, Divide & Conquer) to uncover the bugs in each exercise. Be specific!**

In your explanations, you may want to answer:

- What is the expected vs. actual output?
- If there is a stack trace, what useful information does it contain?
- Which technique did you use, on which line numbers?
- What assumptions did you have about each line of code, and which ones were proven to be wrong?

_Example: I noticed that the program should show pizza orders once a new order is made, and that it wasn't showing any. So, I used the trace forward technique starting on line 13. I discovered the bug on line 27 was caused by a typo of 'pzza' instead of 'pizza'._

_Then I noticed another bug ..._

## Exercise 1

[[Your answer goes here!]]

## Exercise 2

[[Your answer goes here!]]

## Exercise 3

Merge sort:
I expected the output to be a ascending order sorted array. The actual output is an error message. After doing a Trace Forward of the code, I noticed that on line 37, there is a problem with the range. The developer thought that the code for checking if any element is left on the left and right side was more similar then it actually can be. Because of this line 37 tries to access right_side[i], but it doesn't exsist as i = 1 and there is nothing at index 1 of right_side. After solving that we discover that there is a logical error on lines 24 and 27. After having sorted the elements, the developer adds the element at arr[k], however, k is not incremented as the code always resets k to 0. Because of this, the array is sorted in descending order. Finally, as k += 1 is only writen on line 29, once we break out of the while loop on line 22 we do not increment k. Therefore, we need to put a k += 1 for the other two while loops.

Binary search:
I expected the output to be 4, however I was met with a type error. Using the Trace Forward method, I noticed that it broke on line 51 due to a mistake on line 48. The developer assumed that when setting the variable mid, it would be equal to an integer (whole number), however, as it gave an exact (not rounded) answer, it was equal to a float. On line 51 when we try to use mid as an indice, it breaks because indices can't be floats. After fixing this, I noticed another error with the logic in the lines 51-60. The develloper assumes that as they are reassigning the mid, the mid will eventually be equal to the target, or the target is not in the array. However, the target is in the array, it was just never assigned to mid but instead low.
