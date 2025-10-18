# Chapter 2: Finite Automata - The Black Box

## Gathered
- M is an automaton. Written as M = (Q,Σ,δ,q0,F)
- L is a language of words, each of which are a sequence of input symbols.
- Q is the set of states in an automaton.
- Σ is a set of input symbols - e.g. (0,1) or (a,b).
- δ is a transition function that takes in a state and an input symbol, outputting the next state.
- q0 is a starting state.
- F is a set of final states.
- ε transitions can be a transition taken by an automaton without reading an input symbol.

## Question 1

a) Any possible string of a and b, e.g.:
- aaa
- bbb
- abab
- bababa
- abbbbbbbbbbbaaaabb

b) Either 0 or 1.

c) Either any number of 0s or a single 1.

## Question 2

To prove that if language L is accepted by some finite automaton then L^-1^ is also accepted by some finite automaton:

Let there be a language L that can be written by a finite automaton M.
M = (Q, Σ, δ, q0, F)

Thus, assume L^-1^ can be accepted by an automaton M'.
M' = (Q, Σ, δ', q'0, F')

Q and Σ are the same.
δ is flipped.
q0 becomes a final state.
F becomes a starting state.

If we sketched automaton M, flipped the arrows' directions, defined the starting states as final states and vice versa, we would get M'. If there were multiple final states in M, there can be an additional starting state prefixed to the old final states that links to them - i.e. introducing a new start state with ε transitions.

Therefore, L^-1^ can be accepted by automaton M'.

## Question 3

To argue that no finite automaton can accept all palindromes over a given alphabet:

A finite automaton's states merely summarise what it's seen so far. Therefore, there are a finite number of states.

Palindromes require knowledge of the first half of the word in order to reverse it and compare with the second half. This "knowledge" becomes longer with the length of a palindrome, so expressing it would require a way to have an infinite number of distinct states. Therefore, no finite automaton can accept all palindromes over an alphabet with more than one symbol.

## The challenges I faced with this chapter

The first question was fairly trivial. Once you grasp how an automaton works, it just becomes a set of rules following "and" and "or".

The second question was a huge jump in difficulty due to it requiring me to explain this topic using the large amount of notation I was newly introduced to. It took me a very long time - for no reason, since I managed to solve this by drawing and understanding a diagram first.

- Create a diagram flowing from q0 to q1, q2, and q3 and q4 branching from q2.
- Arrows flow into each state.
- L^-1^ would require the δ and initial and final to be inverted, so invert all of the arrows and initial and final states.
- You can only have one initial state, so add another that joins into the old final states with arrows representing ε functions. If there was a single old final state, this is not necessary.

Then it was just testing. Given this, I could trace through each automaton M and M' and generate a list of possible words. It enabled me to compare their outputs, allowing me to create a more formal explanation.

The third question was similar to the second in terms of difficulty - again, due to the nature of the question being one requiring an explanation. Rather than requiring a heavily logical explanation like question 2 was, however, question 3 dug into the heart of how automatons work.

Once again, I found myself wasting time going into logical explanations that reached no conclusion. I reached an answer by taking a step back and just decomposing what I had to do. The first step was truly understanding what a state was. Then I took a similar approach as I did for question 2 and sketched out a few examples: aba, abba, abbba, abbbba, a, b, bab, baab, etc. After noticing the symmetrical nature of these words, I realised how limited states were, leading me to the conclusion that an infinite number of states would be needed to represent every single possible palindrome.
