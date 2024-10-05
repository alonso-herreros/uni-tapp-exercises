## Telematic Applications

# TCP Theory Questions

*Academic year 2024-2025*
*Dr. Daniel Díaz Sánchez*

---

## Question 1
Assuming two machines are connected to the same local area network, if they exchange UDP or TCP
traffic, does fragmentation occur? Indicate in which cases and the reason. Would there be
fragmentation outside the local network?

## Question 2
What is the cause of packet loss in TCP/IP?

## Question 3
In TCP, if a server (receiver) finishes sending data and has nothing else to do, can it send the FIN
without waiting for the sender? What is this called? Can the sender still send more data?

## Question 4
If a server receives an RST in response to its (SYN,ACK) accepting the connection, what happens in
that case? Would the passive socket be closed? Would the (SYN,ACK) be retransmitted? Would a timeout
occur?

## Question 5
What effective window does Nagle authorize when in use for the first segment that is sent if nothing
is pending acknowledgment? When we study slow start and congestion avoidance, return here to
determine which massive traffic algorithm it resembles more: slow start (with what window (cwnd)
value?) or congestion avoidance?

## Question 6
What is WIN used for in a TCP connection? Is the parameter different for the receiver or the sender,
or does it have to be the same?

## Question 7
What is the best window in the absence of flow control limits and without congestion issues? The
largest window, whatever it may be? The smallest possible (what would it be)? The product of
bandwidth and round-trip time ($BW×RTT$)? Why?

> **Answer** ($✓$)
>
> The best is $\frac{RTT}{T_{tx}}$, which is the *continuous sending window*.

## Question 8
What is the RTO? What parameters does the Jacobson algorithm take into account for calculating the
retransmission timer? Why is it necessary to have a good estimate of the RTT?

## Question 9
What does the Karn/Partridge algorithm consist of?

> **Answer** ($✓$)
>
> When you retransmit segments, there is a chance to wrongly estimate the RTO when retransmitting
> segments. The Karn/Partridge algorithm proposes to stop measuring RTT when a segment is
> retransmitted.

## Question 10
Would you say that a TCP receiver can reduce the advertised window size in response to congestion in
the routers along the path?

> **Answer** ($✓$)
>
> No. The receiver window is used for flow control, not congestion control. The congestion window is
> independent of the receiver window.

## Question 11
The fast recovery / fast retransmit mechanism allows the sender to retransmit the lost segment
without waiting for the retransmission timer to expire. How does the window grow until the lost
segment arrives (in slow start or congestion avoidance)?

## Question 12
About TCP windows

### Sub-question 12.a
What is the congestion window (cwnd)? When does its value change?

### Sub-question 12.b
What is the advertised window (WIN)? How do we find its value?

### Sub-question 12.c
What is the effective window? How is it calculated?

### Sub-question 12.d
What is the continuous sending window? How is it calculated?

### Sub-question 12.e
What is the relationship between the windows regarding the number of segments that can be sent per
RTT? (Indicate how each one influences the number of segments sent per RTT)

## Question 13
What do we call the situation in which the rate of data that the sender can transmit is much higher
than what the receiving application can read, and therefore the receiver sends window updates
smaller than half of its buffer and the MSS (in this situation, very small datagrams (tinygrams) are
sent)? How is it avoided?

## Question 14
What is the purpose of the TCP timer called keep-alive?

## Question 15
Suppose that in a TCP connection between A and B, one of the ends (B) is only receiving data and its
receive buffer is full. If the buffer is eventually freed and B sends an acknowledgment indicating
the situation, but the acknowledgment is lost, a deadlock would occur. What mechanism is used in TCP
to prevent this deadlock?
