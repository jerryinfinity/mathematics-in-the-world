## The Pigeonhole principle

The Pigeonhole principle states that if there are $$n+1$$ pigeons, and all of them sits in one of $$n$$ holes, then there has to be a hole that contains *at least* 2 pigeons. More generally, if there are $$mn+1$$ pigeons in $$n$$ holes, there must be a hole that contains at least $$m+1$$ pigeons.

This argument was popularized by [Peter Gustav Lejeune Dirichlet](http://en.wikipedia.org/wiki/Peter_Gustav_Lejeune_Dirichlet) in 1834. It is also common to refer to the idea as Dirichlet's principle or the Dirichlet principle.

(TODO: Tell the story about the inhabitants of Paris.)


### Dividing the difference

> Given $$n + 1$$ integers, there exists a pair $$a, b$$ such that $$n$$ divides $$a-b$$.

The most crucial step in applying the Dirichlet principle is identifying what plays the role of the pigeons and holes. In this problem, the pigeons are clearly the $$n+1$$ integers. To get the argument through, we need to pick $$n$$ holes. Let us choose these to be the numberts between $$0$$ and $$n-1$$ inclusive, that is, the possible *remainders* when dividing an integer by $$n$$. (Note that the remainder of $$-1$$ is $$n-1$$.) Under this scheme, each of the possible $$n+1$$ integers we started with will be associated with its remainder. Ditichlet's principle implies there are at least two integers with the samme remainder, and hence their difference must be divisible by $$n$$.

The idea of using the remainders is a very powerful tool in mathematics. Let us introduce then some notation. The remainder of a number when divided by $$n$$ will be called its *congruence class modulo* $$n$$. Whenever two numbers $$a$$ and $$b$$ have the same congruence class modulo $$n$$, we will say they are *coungruent* modulo $$n$$ and write write $$a \equiv b \pmod{n}$$.


### Summing to 10

> For every 6-element subset $$S$$ of $$\{ 1, \dots, 9 \}$$, there exists a pair of distinct integers $$a, b \in S$$ such that $$a + b = 10$$.

Let us create the boxes in a way that could help us for this problem, is such a way elements in the same box will sum to 10. The first box will be $$\{1,9\}$$, the second $$\{2,8\}$$, then $$\{3,7\}$$ and $$\{4,6\}$$, and at last the element 5 alone, $$\{5\}$$. We have now 6 integers in 5 boxes, so there is at least one box that contains two elements; this box cannot be $$\{5\}$$, that contains only one element, so it has to be one of the others. This then proves that there are two integers whose sum is 10.


### We have the same number of friends!

> Is it possible that at a party all guests have different numbers of friends attending?

SOLUTION ONE: Let us say the number of people attending the party is $$n$$. The possibilities for the number of friends that people can have at the party are from 0 (in case somebody does not know anybody else) to $$n-1$$ (for someone knowing everybody else); this gives us $$n$$ possibilities. We have then $$n$$ people-pigeons, and $$n$$ possibilities-holes: so, we *cannot* conclude that there are two people with the same number of acquaintances. We need to also analyze the possibility that there is exactly one person knowing nobody else, one person knowing exactly one other, one person knowing two, and so on until exactly one person that knows anybody else. But this is not possible, because if there is a person $$A$$ not knowing anybody, there cannot be a person $$B$$ that knows anybody else, because it cannot know $$A$$! Rephrasing this, we can "group" together as we did in the previous exercise in the same box the possibilities $$\{0,n-1\}$$, and we know that at most one possibilities in this box will be achieved; we are then in the situation of $$n-1$$ boxes, with $$n$$ people, and we get that there are two people having the same number of friends.

SOLUTION TWO: We can use induction; suppose we know that for any group of $$n-1$$ people there are two that have the same number of friends. Let us consider the situation with $$n$$ people: at first, suppose there is a person $$A_0$$ knowing 0 people; then, we can consider the other $$n-1$$ people, that are in some sense "disconnected" from $$A_0$$, and restrict the problem to them: from what we said at the beginning, we then know that there are two people among those that have the same number of friends. On the other hand, consider the opposite situation, where we have nobody having 0 friends; then we can apply the Dirichlet principle, because we have $$n$$ people, and $$n-1$$ possibilities for the number of friends they have (the numbers from 1 to $$n-1$$).
To conclude the proof by induction, we need to do what is called "proving the base case": suppose that we have two people (the simplest that this problem can be, because with one person the problem does not make sense), that let us prove our statement: the only two possibilities here are that they know each other, or that they don't; in both cases, they have the same number of friends, so the claim follows.


### The Friendship Theorem

> Given a group of six people, show that there always exist three such that either
> * all know each other, or
> * none of them are acquaintances.

This problem is very tricky; let us pick one of the six people $$A$$, let's analyze her relationships with the other 5. We need to consider as boxes the possible relationships with $$A$$ (knowing $$A$$, not knowing $$A$$) and as pigeons the five people. By Dirichlet principle, then, there are at least three people $$B, C$$ and $$D$$ that are in the same relationship with $$A$$. Let us say at first that they all know $$A$$; in this case, either two of them know each other (and hence together with $$A$$ they form a triple of people that all know each other) or there is no couple of them that know each other (and in such case $$B,C,D$$ form of a triple that has no acquaintances), that concludes this case. The case in which $$B,C$$ and $$D$$ do not know $$A$$ is exactly the same, because the problem is symmetrical - that means, we can change the relationship between every couple of people (knowing to not knowing, and vice versa), and we would be asking for the same thing - so it is true as well.

REMARK-MATH-HISTORY: In the same way, going a couple of steps further, we can prove the same result that among 18 people there are 4 that either all know each other, or are not acquainted at all. But what about 17? What is the \texiti{minimum} number such that this situation occurs? These solutions to this problem are called Ramsey numbers - for instance, for instance, this exercise was asking to prove $$R(3,3)$$ is at most 6. The fact that $$R(4,4)=18$$ required an extended check using a computer of all $$2.46\times 10^{26}$$ possibilities. The only thing we know nowadays about $$R(5,5)$$ is that it lies between 43 and 49 included. About this, mathematician Joel Spencer has an anecdote about Paul Erd\:os, an hungarian mathematician that spent many years working on this kind of problems:

Erdős asks us to imagine an alien force, vastly more powerful than us, landing on Earth and demanding the value of R(5, 5) or they will destroy our planet. In that case, he claims, we should marshal all our computers and all our mathematicians and attempt to find the value. But suppose, instead, that they ask for R(6, 6). In that case, he believes, we should attempt to destroy the aliens.


### The square orchard

> You own a small orchard containing 51 trees. The shape of the garden is a square with side length 70 meters. It is possible to use a circular fence of radius 10 meters to enclose at least 3 of the trees?

The statement of this problems reminds us immediately of Dirichlet theorem; we have 51 trees-pigeons, and we want 3 to be close enough to be contained in a circle of radius 10. We can apply some reverse psychology to this problem: how many boxes do we need in such a way at least 3 of the 51 are in the same box? The answer is 25 (we need to solve $$mn+1=51$$ and $$m+1=3$$ to find $$n$$). This tells us that if we divide the square in 25 regions, then there is a region that contains 3 trees. For obvious reasons, we cannot split a square in 25 circles of radius 10, there's no way we can have the boundaries to adhere one each other. We can though try to divide the square in 25 regions each of which is *contained* in a circle of radius 10, and the obvious choice is to divide it in 25 smaller squares of radius 70/5=14. Now, the biggest square that is contained in a circle of radius 10 has side $$10\cdot\sqrt{2}\sim 14.14$$, so a circle of radius 10 can indeed contain a square of side 14. Wrapping everything up, recall that we found out that there is one of the little squares that contains at least 3 trees, that gives us that there is also a circle of radius 10 containing them.

