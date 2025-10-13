---
layout: post
title:  "Trying to build an intuition for Barrington's theorem"
date:   2025-10-11 12:06:00 -0400
categories: cs-theory
---

# What is Barrington's Theorem?

I find Barrington's Theorem to be one of the most beautiful pieces of mathematics ever discovered. It's simple to state, the proof is only a couple pages long, yet it elucidates a connection that was highly surprising at the time of publication and (important to this blog post) still evades my intuitive understanding. First, let's define some terms.

$$NC^1$$ is the class of decision problems that can be recognized by log-depth boolean circuits where each gate has fan-in 2. It contains addition, subtraction, multiplication, division, sorting lists of numbers, and the majority function -- given $$n$$ bits, are most of them 1?

A _group program_ over some group $G$ is also a model of computation. A group program is comprised of a list of elements from $G$, each raised to the power of an input bit. In other words, a group program maintains a single element as an accumulator; instructions take the form of "check a particular input bit; if it is 1, then apply this element from $G$ to your accumulator."

$$S_5$$ is the symmetric group over 5 objects. It has 5! = 120 elements, which we will write in cycle notation. For example, $$(1 2 3 4 5)$$ is the permutation that sends 1 to 2, 2 to 3, 3 to 4, 4 to 5, and 5 back to 1. Note that any such permutation can be broken down into a set of pairwise swaps. For any permutation, we can ask whether the number of swaps it breaks down into is odd or even; it turns out this is a consistent property of any given permutation. Then, $$A_5$$ is the group consisting of only even permutations of 5 objects. $$A_5$$ also corresponds to the group of rotational symmetries of the icosahedron.

This gives us enough mathematical background to state Barrington's Theorem: group programs over $$A_5$$ capture exactly $$NC^1$$.

# What's so unintuitive about this?

Consider our computational model -- a group program over $$A_5$$ -- personified as an oracle with an icosahedron whose orientation is preserved. We have a set of 100 bits, and we want to know if any of them are 1 -- the humble $$OR$$ function. No problem, says the oracle. They begin with the die landed on 1, and they read the bits one by one. If at any point they find a bit that is on, they increment the die to 2 and skip past the rest of the inputs. Once the bits have all been enumerated, they simply check if the die reads 1 or 2, and that's the answer.

We then bring another 100 bits to our oracle, and now we want to know if at least 19 of them are 1. Again, no problem, as a similar scheme suffices, incrementing the die's face every time a 1 is found, with the result read off at the end. We could even extend this to 59 bits by using the orientation of the dice to count.

But then we bring 1000 bits to the oracle, and we wish to know if at least 501 of them are on. Simple counting no longer works, as there aren't enough orientations of the die to store the current count. Things seem hopeless, and yet, Barrington's Theorem says the oracle has a way out here. This is the intuition I lack. How can the oracle efficiently count with only a constant amount of memory?

# The theoretical construction

The theoretical construction comes in two steps. First, we put $$MAJORITY$$ into $$NC^1$$; then, we put $$NC^1$$ into our $$A_5$$ program.

Putting $$MAJORITY$$ into $$NC^1$$ is done via iterated addition, which we do first via addition.

To add in $$NC^1$$, we use a carry-lookahead adder (which really puts addition into $$AC^0$$). Note that when adding, the carryless addition only depends on the two input bits at that index, and we can calculate the carry at that index as an $$OR$$ of $$AND$$s (basically, we have a carry at our index if it has carried all the way from any prior index). We can then implement those $$n$$-wide $$AND$$s and $$OR$$s as log-depth trees, placing addition into $$NC^1$$.

To do iterated addition, can we simply make a tree of these operations? Our input length is $$n$$, and our additions at the bottom of the tree will have a constant depth. But as we go up the tree, if we let our overflows accumulate, the top additions will add numbers of length $$O(\log(n))$$, and therefore will have depth $$O(\log\log(n))$$, and since our addition tree is already of depth $$O(\log(n))$$, we will have a total depth of $$O(\log(n)\log\log(n))$$.

So instead, to create iterated addition, we have to do the 3-to-2 compression trick -- convert $$X + Y + Z = A + B$$, where $$A$$ becomes the direct sum and $$B$$ becomes a word with all of the immediate carries. You do this compression over and over again, and each compression is in $$NC^0$$, so a log-depth tree of them is fine, followed by a single addition in $$NC^1$$.

Finally, we apply Barrington's Theorem, which boils down to the following:
* We can encode constants and input checks as straightforward group programs
* If we have a group program, $$NOT$$ is easy
* (Here's the nontrivial part) If we have two group programs, we can leverage the unsolvability of $$A_5$$ to $$AND$$ those two programs together in constant memory.

We then combine all of this to get our oracle's solution.


