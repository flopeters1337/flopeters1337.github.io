---
title: "Engel's Algorithm for Absorbing States in Markov Chains"
header:
    teaser: assets/images/engel-algorithm-teaser.jpg
    overlay_image: assets/images/engel-algorithm-teaser.jpg
    overlay_filter: 0.3
    caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
    show_overlay_excerpt: false
tags: stochastics probability mathematics programming
---
Recently, I needed an algorithm to compute the hit probabilities of absorbing states in Markov chains. The traditional way to compute them is to make use of the chain's transition probability matrix, $P$ and perform TODOTODOTODO

## Introduction

There is however a neat little cooking recipe in the special case where all the transition probabilities can be expressed as rational numbers. That is to say, each probability of leaving an arbitrary state $i$ and entering another state $j$ can be expressed as

$$P_{ij} = \frac{r_{ij}}{r_i}$$

The master chef who owns the credit to this probabilistic delicacy is the German mathematician [Arthur Engel](https://en.wikipedia.org/wiki/Arthur_Engel_(mathematician)) and in this post, I will show you exactly how you can cook up some delicious probabilities using his recipe.

## Ingredients

Let's begin with some definitions. Suppose that we exist in an abstract world where everything is made up of Markov chains. "But", you may object, "What _are_ Markov chains?". In essence, Markov chains are similar to state machines in the sense that they also concern states and transitions. The catch is that those transitions are not necessarily ___deterministic___. Let me elaborate.

Let's imagine that you begin your life in this strange abstract world in a given state say, for instance, the state "_Not hungry_".

**INSERT IMAGE OF NOT HUNGRY STATE**

Over time, your state might or might not change seemingly at random. You may end up quite peckish after some time has passed. But generally, you will tend to stay in the "_Not hungry_" state. This is because the probability of transitioning from state "_Not hungry_" to itself is quite high, say 85%. We can infer that the probability of transitioning to the state "_Peckish_" from "_Not hungry_" is 15%. This would give us the following Markov chain :

**INSERT IMAGE OF CHAIN**

And we can repeat this process to add yet another state, "_Famished_":

**INSERT IMAGE OF FULL CHAIN**

Of course, this is a very simple Markov chain. Sometimes in this strange probabilistic world, the chains can look a bit more complicated...

**INSERT IMAGE OF COMPLICATED CHAIN**

To describe Markov chains efficiently, we can represent them using their corresponding ***transition matrix***. If the chain has $N$ states, the transition matrix will be of size $N \times N$. The element $T_{ij}$ of this matrix is simply the probability of going from state $i$ to state $j$. Avid readers will be quick to point out that in order to be valid, the sum of all the elements on each row must be equal to 1.

Going back to our hunger Markov chain, we will label the states using numbers (because numbers are fun and keep everything neat and organized!) :

1. *Not hungry*
2. *Peckish*
3. *Famished*
4. *Starving*

Then the corresponding transition matrix will be

$$T =
\begin{pmatrix}
0.8 & 0.2 & 0 & 0 \\
0.1 & 0.7 & 0.2 & 0 \\
0.3 & 0 & 0.5 & 0.2 \\
0.8 & 0 & 0 & 0.2
\end{pmatrix}$$

## Main Course

## Dessert

$b_i < r_i$ for $i \neq u$ and $b_u = r_u$.
