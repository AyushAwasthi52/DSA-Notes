
Time Complexity:
What time complexity to expect based on the value of n

| n             | Possible Complexities      |
| ------------- | -------------------------- |
| $n <= 10$     | $O(n!), O(n^7), O(n^6)$    |
| $n <= 20$     | $O(2^n*n), O(n^5)$         |
| $n <= 80$     | $O(n^4)$                   |
| $n <= 400$    | $O(n^3)$                   |
| $n <= 7500$   | $O(n^2)$                   |
| $n <= 7*10^4$ | $O(n*\sqrt{n})$            |
| $n <= 5*10^5$ | $O(n*logn)$                |
| $n <= 5*10^6$ | $O(n)$                     |
| $n <= 10^18$  | $O(log^2n), O(logn), O(1)$ |


Always keep in mind that insertion and erasure in the middle of an  array is an operation that is performed in $O(n)$ time complexity.

