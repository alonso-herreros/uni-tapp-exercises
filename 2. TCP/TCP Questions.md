## Question 7

What is the best window in the absence of flow control limits and without congestion
issues? The largest window, whatever it may be? The smallest possible (what would
it be)? The product of bandwidth and round-trip time ($BW^1×RTT$)? Why?

> **Answer**
>
> The best is $\frac{RTT}{T_{tx}}$, which is the *continuous sending window*.

## Question 9
What does the Karn/Partridge algorithm consist of?

> **Answer**
>
> When you retransmit segments, there is a chance to wrongly estimate the RTO when retransmitting
> segments. The Karn/Partridge algorithm proposes to stop measuring RTT when a segment is
> retransmitted.

## Question 10
Would you say that a TCP receiver can reduce the advertised window size in response
to congestion in the routers along the path?

> **Answer**
>
> No. The receiver window is used for flow control, not congestion control. The congestion window is
> independent of the receiver window.
