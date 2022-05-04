---
title: "Engel's Algorithm for Markov Chains #1: Appetizer"
header:
    teaser: assets/images/engel-algorithm-teaser.jpg
    overlay_image: assets/images/engel-algorithm-teaser.jpg
    overlay_filter: 0.3
    caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
    show_overlay_excerpt: false
tags: stochastics probability mathematics programming
---
Recently, I needed an algorithm to compute the hiting probabilities of absorbing states in Markov chains. The traditional way to compute them is to make use of the transition probability matrix, $$ P $$ and perform a typical LU decomposition to get the hitting probabilities.

On the plus side, it's a very straightforward way to get hitting probabilities.

On the downside, LU decomposition is _hard_.

Like, $$ O(n^3) $$ kind of hard.

There is however a neat little cooking recipe in the special case where all the transition probabilities can be expressed as rational numbers. That is to say, each probability of leaving an arbitrary state $$ i $$ and entering another state $$ j $$ can be expressed as

$$P_{ij} = \frac{r_{ij}}{r_i}$$

The master chef who owns the credit to this probabilistic delicacy is the German mathematician [Arthur Engel](https://en.wikipedia.org/wiki/Arthur_Engel_(mathematician)) and in this collection of posts, I will show you exactly how you can cook up some delicious probabilities using his recipe. Let's heat up the oven!

## Markov Chains: Definitely Definitive Definitions

Suppose that we exist in an abstract world where everything is made up of Markov chains. "_But_", you may object in your abstract ethereal nature, "_What are Markov chains?_". In essence, Markov chains are similar to state machines in the sense that they also concern states and transitions. The catch is that those transitions are not necessarily ___deterministic___. Let me elaborate.

Let's imagine that you begin your life in this strange abstract world in a given state say, for instance, the state "_Not hungry_".

**INSERT IMAGE OF NOT HUNGRY STATE**

Over time, your state might or might not change seemingly at random. You may end up quite peckish after some time has passed. But generally, you will tend to stay in the "_Not hungry_" state. This is because the probability of transitioning from state "_Not hungry_" to itself is quite high, say 80%. We can infer that the probability of transitioning to the state "_Peckish_" from "_Not hungry_" is 20%. Now if you're peckish, there's a good change you'll start eating the cookie dough before it's done cooking to return to the "_Not hungry_" state. Let's say we're trying to model somebody on a diet. The probability they would eat the cookie dough would be something close to 10%. We can also model that they would remain in the "_Peckish_" state for a probability of 90%. This would give us the following Markov chain :

**INSERT IMAGE OF CHAIN**

And we can repeat this process to add yet another state, "_Famished_":

**INSERT IMAGE OF FULL CHAIN**

Of course, this is a very simple Markov chain. Sometimes in this strange probabilistic world, the chains can look a bit more complicated...

**INSERT IMAGE OF COMPLICATED CHAIN**

To describe Markov chains efficiently, we can represent them using their corresponding ___transition matrix___. If the chain has $$ N $$ states, the transition matrix will be of size $$ N \times N $$. The element $$ T_{ij} $$ of this matrix is simply the probability of going from state $$ i $$ to state $$ j $$. Avid readers will be quick to point out that in order to be valid, the sum of all the elements on each row must be equal to 1 following Kolmogorov's second axiom.

Going back to our hunger Markov chain, we will label the states using numbers (because numbers are fun and keep everything neat and organized!) :

1. _Not hungry_
2. _Peckish_
3. _Famished_
4. _Starving_

Then the corresponding transition matrix will be

$$T =
\begin{pmatrix}
0.8 & 0.2 & 0 & 0 \\
0.1 & 0.7 & 0.2 & 0 \\
0.3 & 0 & 0.5 & 0.2 \\
0.8 & 0 & 0 & 0.2
\end{pmatrix}$$
