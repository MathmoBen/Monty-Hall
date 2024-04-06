# Monty-Hall

Some thoughts on the Monty Hall Problem.

For those who don't know, Monty Hall was a game show host in the 1960s. The game works like this. You choose 1 of 3 doors, only 1 of which has the prize behind it. Monty then opens one of the other doors revealing a booby prize before giving you the chance to switch your choice to the other unopened door in the hope of finding the prize behind there instead.

Should you switch doors? In particular, what is the probability that switching leads to you winning the prize?

There are many ways of approaching this. Intuitively you definitely should switch - what if there were a million doors and Monty opened not 1 but 999,998 of them i.e. everything but your first choice and 1 other? Suddenly that other door looks rather suspicious - you definitely should switch. Probabilitic calculations tend to get rather involved, often invoke Bayes' Theorem and don't generalise without getting very complicated very quickly.

But it's much simpler than this. If you think about it, switching doors leads to you finding the prize if *and only if* you initially chose incorrectly. The probability of switching leading to a win is thus equal to the probability that you initially chose incorrectly. This is much simpler to work out: as 2 of the 3 doors have booby prizes behind them, the probability that you initially chose wrong is 2/3.

But what if there are not 3 doors but 4 and Monty only opens 1 of them? Now the argument of the last paragraph breaks down - the words "and only if" are now wrong. Instead we must use something that, again, is much simpler than Bayes' Theorem but is still important and useful: the Theorem of Total Probability. It works like this. Let $S$ be the event that switching leads to a win, $C$ the event that you initially chose correctly and $I$ the event that you initially chose incorrectly. Write $P(A)$ for the probability of event $A$ and $P(A|B)$ for the probability of event $A$ given $B$. The Theorem of Total Probability tells us that
$$
P(S) = P(S|C)P(C) + P(S|I)P(I).
$$
In our problem this quickly simplifies: $P(S|C)=0$ since initially choosing correctly and then switching away from that door is guaranteed to give us the booby prize. Hence 
\[
P(S) = P(S|I)P(I).
\]
If there are 4 doors, then since there is only one prize we must have that P(I) = 3/4. Since there are only 2 doors to switch to (of the original 4, you can't switch to your original choice or to the door that Monty opened leaving just 4-2=2 possibilities) it follows that $P(S|I) = 1/2$. We thus have that $P(S)=3/8$ - suddenly switching is no longer a good idea.

But the real beauty of this elegant argument is how easily it generalises - if there are $n$ doors, then we still have that
\[
P(S|C)=0 
\]
but now 
\[
P(I) = (n-1)/n and P(S|I) = 1/(n-2) 
\]
so
\[
P(S) = (n-1)/n(n-2) 
\]
and as $n$ grows larger switching doors looks like an increasingly unappealing option.

Clearly this gets more involved if there are $k>1$ prizes and Monty opens $r<n-k-1$ doors, but that's a story for another post. 

In this repository we record some computations relating to this.
