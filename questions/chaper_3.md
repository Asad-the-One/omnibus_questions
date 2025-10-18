# Chapter 3: Systems of Logic - Boolean Bases

## Question 1:

To show NOR is a complete base all by itself:

In order to prove a function is a complete base, it should be able to express AND/OR and NOT. Thus:

- AND itself is not a complete base, as if there is a single 0 in inputs, you can never output 1.
- OR itself is not a complete base, as if there is a single 1 in inputs, you can never output 0.
- NOT itself is not a complete base, as it only takes one input.

NOR can be expressed as "NOT (A OR B)".

- We can express NOT with A NOR A.

- We can express A AND B as (A NOR A) NOR (B NOR B).

Therefore, NOR is functionally complete.

If we wanted to, we can express A OR B as ((A NOR A) NOR (B NOR B)) NOR ((A NOR A) NOR (B NOR B))

## Question 2

To show {AND, EQUIVALANCE, XOR} is functionally complete:

EQUIVALENCE is 1 for 1 1 and 0 0.

XOR is 1 for 0 1 and 1 0.

AND is 1 for 1 1.

We only need to express NOT to show this set is functionally complete, as AND is in the set.

NOT A = A EQUIVALENCE (A XOR A)

Therefore, the set is functionally complete.

## Question 3

s0 s1
0 0  0 A
1 0 1 B
0 1 2 C
1 1 3 D

- 0: A AND NOT S0 AND NOT S1
- 1: B AND S0 AND NOT S1
- 2: C AND NOT S0 AND S1
- 3: D AND S1 AND S2

The multiplexer takes all of these and inputs them into OR. Therefore:

F = (A AND NOT S0 AND NOT S1) OR (B AND S0 AND NOT S1) OR (C AND NOT S0 AND NOT S1) OR (D AND S1 AND S2)

NAND = NOT (X AND Y)

To express F in terms of NAND, substitude E and F as S0 and S1 for simplicity. Now expand into more brackets:

F = A∧(¬E∧¬F) v B∧(E∧¬F) v C∧(¬E∧F) v D∧(E∧F)

AND, OR and NOT in terms of NAND:

- (x | y) | (x | y)
- (x | x) | (y | y)
- (x | y)

Best to work from inside out. Start with NOTs, then ANDs, then ANDs again, group pairs, then ORs, then ORs again.

Apply NOTs:

F = A∧((E|E)∧(F|F)) v B∧(E∧(F|F)) v C∧((E|E)∧F) v D∧(E∧F)

Apply ANDs:

F = A∧(((E|E)|(F|F))|((E|E)|(F|F))) v B∧((E|(F|F))|(E|(F|F))) v C∧(((E|E)|F)|((E|E)|F)) v D∧((E|F)|(E|F))

Apply ANDs again (pre-emptively adding brackets around pairs for the next step):

F = ((A|(((E|E)|(F|F))|((E|E)|(F|F))))|(A|(((E|E)|(F|F))|((E|E)|(F|F)))) v (B|((E|(F|F))|(E|(F|F))))|(B|((E|(F|F))|(E|(F|F))))) v ((C|(((E|E)|F)|((E|E)|F)))|(C|(((E|E)|F)|((E|E)|F))) v (D|((E|F)|(E|F)))|(D|((E|F)|(E|F))))

Let:

- g = (A|(((E|E)|(F|F))|((E|E)|(F|F))))|(A|(((E|E)|(F|F))|((E|E)|(F|F)))
- h = (B|((E|(F|F))|(E|(F|F))))|(B|((E|(F|F))|(E|(F|F)))))
- i = (C|(((E|E)|F)|((E|E)|F)))|(C|(((E|E)|F)|((E|E)|F))
- j = (D|((E|F)|(E|F)))|(D|((E|F)|(E|F))))

F = (g v h) v (i v j)

Apply ORs:

F = ((g|g)|(h|h)) v ((i|i)|(j|j))

Apply OR:

F = (((g|g)|(h|h))|((g|g)|(h|h)))|(((i|i)|(j|j))|((i|i)|(j|j)))

Expand:

F = ((((A|(((E|E)|(F|F))|((E|E)|(F|F))))|(A|(((E|E)|(F|F))|((E|E)|(F|F)))|(A|(((E|E)|(F|F))|((E|E)|(F|F))))|(A|(((E|E)|(F|F))|((E|E)|(F|F))))|((B|((E|(F|F))|(E|(F|F))))|(B|((E|(F|F))|(E|(F|F)))))|(B|((E|(F|F))|(E|(F|F))))|(B|((E|(F|F))|(E|(F|F)))))))|(((A|(((E|E)|(F|F))|((E|E)|(F|F))))|(A|(((E|E)|(F|F))|((E|E)|(F|F)))|(A|(((E|E)|(F|F))|((E|E)|(F|F))))|(A|(((E|E)|(F|F))|((E|E)|(F|F))))|((B|((E|(F|F))|(E|(F|F))))|(B|((E|(F|F))|(E|(F|F)))))|(B|((E|(F|F))|(E|(F|F))))|(B|((E|(F|F))|(E|(F|F))))))))|((((C|(((E|E)|F)|((E|E)|F)))|(C|(((E|E)|F)|((E|E)|F))|(C|(((E|E)|F)|((E|E)|F)))|(C|(((E|E)|F)|((E|E)|F)))|((D|((E|F)|(E|F)))|(D|((E|F)|(E|F))))|(D|((E|F)|(E|F)))|(D|((E|F)|(E|F))))))|(((C|(((E|E)|F)|((E|E)|F)))|(C|(((E|E)|F)|((E|E)|F))|(C|(((E|E)|F)|((E|E)|F)))|(C|(((E|E)|F)|((E|E)|F)))|((D|((E|F)|(E|F)))|(D|((E|F)|(E|F))))|(D|((E|F)|(E|F)))|(D|((E|F)|(E|F)))))))

Replace with S0 and S1:

F = ((((A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1))))|(A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1)))|(A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1))))|(A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1))))|((B|((S0|(S1|S1))|(S0|(S1|S1))))|(B|((S0|(S1|S1))|(S0|(S1|S1)))))|(B|((S0|(S1|S1))|(S0|(S1|S1))))|(B|((S0|(S1|S1))|(S0|(S1|S1)))))))|(((A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1))))|(A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1)))|(A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1))))|(A|(((S0|S0)|(S1|S1))|((S0|S0)|(S1|S1))))|((B|((S0|(S1|S1))|(S0|(S1|S1))))|(B|((S0|(S1|S1))|(S0|(S1|S1)))))|(B|((S0|(S1|S1))|(S0|(S1|S1))))|(B|((S0|(S1|S1))|(S0|(S1|S1))))))))|((((C|(((S0|S0)|S1)|((S0|S0)|S1)))|(C|(((S0|S0)|S1)|((S0|S0)|S1))|(C|(((S0|S0)|S1)|((S0|S0)|S1)))|(C|(((S0|S0)|S1)|((S0|S0)|S1)))|((D|((S0|S1)|(S0|S1)))|(D|((S0|S1)|(S0|S1))))|(D|((S0|S1)|(S0|S1)))|(D|((S0|S1)|(S0|S1))))))|(((C|(((S0|S0)|S1)|((S0|S0)|S1)))|(C|(((S0|S0)|S1)|((S0|S0)|S1))|(C|(((S0|S0)|S1)|((S0|S0)|S1)))|(C|(((S0|S0)|S1)|((S0|S0)|S1)))|((D|((S0|S1)|(S0|S1)))|(D|((S0|S1)|(S0|S1))))|(D|((S0|S1)|(S0|S1)))|(D|((S0|S1)|(S0|S1)))))))

(
This took so long.
Extremely unreadable. Probably should have added spaces
Checked on VSCode and the brackets miraculously line up perfectly - yippee :D
Rechecked my working and it logically checks out
In hindsight, using F as a substitute for S1 may not have been a good idea since I defined the function as F
)

This is not the simplest NAND circuit. It is an expanded form of the original that has a lot of repetition. Some outputs, such as E|E and F|F can be computed once into variables with names such as T, U, and V, then used as inputs to avoid recomputing the same expression over and over again. Even expressions like (S0|S0)|(S1|S1) are repeated. The same logic applies, however - e.g. compute S0|S0 and provide it as T, compute S1|S1 and provide it as U, then compute T|U (an equivalent statement) and provide it as V.

## The challenges I faced with this chapter

This wasn't a particularly challenging chapter in hindsight. It took me a while to answer question 1, as I couldn't understand the request - what is meant by a complete base? Once I figured it out, it was merely a matter of sketching truth tables to compute expressions for AND/OR and NOT. I managed to convince myself that if a function is true for AND and NOT, it's also true for OR and NOT (and vice versa).

Given this, I managed to complete question 1. Then question 2 was also a breeze. Question 3 is logically very easy. It just took an immensely long time to produce that behemoth of a multiplexer statement. Subsitution techniques helped immensely.
