# Theory of Computation  
**Author:** Matteo Ghilardini

---

## Assignment 1
### Problem 1

This Turing Machine operates over the alphabet $\{0,1\}$ and recognizes strings belonging to the language $\{0^n 1^m \lor 1^m 0^n | m=n\}$, meaning it accepts strings that consist of an equal number of `0`s and `1`s.

![problem1](Diagrams/prob1.png)

The machine begins in the `start` state, where it examines the first symbol. If it encounters a $0$, it replaces it with an $x$ and moves right into the `have0` state, indicating that it has started processing a sequence of $0s$ and so is _looking for_ a $1$. Similarly, if it encounters a $1$, it marks it as $y$ and transitions to the `have1` state, signaling the start of a sequence of $1s$ and so is _looking for_ a $0$. If the machine encounters an already marked symbol ($x$ or $y$), it continues moving right to verify the structure of the string. When it reaches a blank space (`' '`), it moves left into the `accept` state, confirming that the input is valid; this makes also the input `' '` string accepted.

In the `have0` state, the machine scans right through $0s$, as well as marked symbols $x$ and $y$. When it encounters a $1$, it marks it as $y$ and moves left to the `back` state to repeat the process. If it reaches a blank space, it means there are more $0s$ than $1s$, leading the machine to reject the input.

The `have1` state operates in a similar way. The machine moves right, passing over $1s$, $xs$, and $ys$. When it encounters a $0$, it marks it as $x$ and moves left to the `back` state. If it reaches a blank space, it indicates that there are more $1s$ than $0s$, causing the machine to reject the input.

The `back` state allows the machine to return leftward, scanning past $0s$, $1s$, $xs$, and $ys$ until it reaches the beginning of the string. If it encounters a blank space, it moves right back into the `start` state, repeating the process until all symbols have been marked.

If all $0s$ and $1s$ have been correctly paired and marked, reaching a blank space leads the machine into the `accept` state, meaning the input is valid. However, if there is an imbalance in the number of $0s$ and $1s$, the machine transitions into the `reject` state.


### Problem 2