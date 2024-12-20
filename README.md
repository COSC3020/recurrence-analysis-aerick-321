# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Base case divides n until n <= 1. Calls mystery function 3 times and inside is n/3. The complexity of the loops are $O(n^5)$ so the recurrance relation is $T(n) = 3T(n/3) + n^5$. 

$T(n) = 3(3T (n/9) + (n/3)^5) + n^5 $

$T(n) = 9T(n/9) +(n/3)^5 + n^5$

$T(n) = 9(3T (n/27) +(n/9)^5) +(n/3)^5 + n^5$

$T(n) =3^i T(n/3^i)$ + $\sum_{j=0}^{i-1} 3^j/{3^{5^j}} *n^5$

$n/3^i$ = 1

i = log3n

$T(n) =3^{log3n} T(n/3^{log3n})$ + $\sum_{j=0}^{log3n-1} 3^j/{3^{5^j}} *n^5$

$n *1 +((n-1) /2) *n^5$

simplifies to n + $n^5$

Solving the recurrence relation you get $T(n) ∈ O(n^5)$

Geeksforgeeks.com for review on recurrence relations. “I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.”
