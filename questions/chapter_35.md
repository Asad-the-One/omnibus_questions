# Chapter 35: Sequential Sorting - A Lower Bound on Speed

## Question 1

For bubble sort: the worst-case complexity of this algorithm is O(n^2^). Due to the algorithm having nested "for" loops, it cannot realise O(nlogn), as it doesn't significantly reduce the amount of data in each iteration (e.g. like a binary search does, halving data numbers on each iteration).

## Question 2

Given a list [x,y,z]:

Can draw on paper. May upload image later, but I have compared it to an internet search, and it's right.

## Challenges I faced with this chapter

This chapter was particularly simple. It required knowledge of big O notation and how you get an expression from an algorithm. Bubble sort has the following structure:

for
    for
        if
    if then break

That 4th line gives the best case scenario of O(n), as if it's satisfied on the first iteration, it means the list was already sorted, and no swaps were made.

The second question took me a while. It required my understanding of the method of drawing a decision tree shown in the book, along with some research on Google that showed me a different way of laying out, in which the bubbles contained boolean equations branching into True and False rather than L0, L1, etc branching off into boolean equations. I ultimately managed to understand Dewdney's method, and got a diagram out.