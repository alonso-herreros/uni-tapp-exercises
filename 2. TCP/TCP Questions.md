## Telematic Applications

# TCP Theory Questions

*Academic year 2024-2025*
*Dr. Daniel Díaz Sánchez*

---

## Question 1
Assuming two machines are connected to the same local area network, if they exchange UDP or TCP
traffic, does fragmentation occur? Indicate in which cases and the reason. Would there be
fragmentation outside the local network?

> **Answer**
>
> In the case of UDP, there is no connection and no MTU discovery, so fragmentation may occur if
> segments are too big. This may happen within the LAN and outside too.
>
> In TCP, there should be no fragmentation as long as the Path MTU Discovery protocol works
> correctly. However, if there are changes in the network and the traffic in an existing connection
> has to be redirected through a path with a lower MTU, the network layer may need to fragment the
> segments before sending them. If the traffic's scope extends out of the LAN, and the Path MTU
> Discovery protocol works, there should be no fragmentation either. However, the same problem as
> before may arise.

## Question 2
What is the cause of packet loss in TCP/IP?

> **Answer**
>
> The main cause of packet loss is congestion, which causes packet drops due to filled router or
> switch buffers

## Question 3
In TCP, if a server (receiver) finishes sending data and has nothing else to do, can it send the FIN
without waiting for the sender? What is this called? Can the sender still send more data?

> **Answer**
>
> Yes, this is called a half-close. If one side wants to stop sending data, it can send FIN. It will
> be able to keep receiving data from the other side and sending back ACKs, but it shouldn't send
> any new data

## Question 4
If a server receives an RST in response to its (SYN,ACK) accepting the connection, what happens in
that case? Would the passive socket be closed? Would the (SYN,ACK) be retransmitted? Would a timeout
occur?

> **Answer**
>
> If one side receives an RST, it must assume the other side is forced to close the connection, and
> it must set that socket as closed.
>
> The passive socket that listens for new connections
> does not need to be closed in this case, as new connections from the same client or other clients
> could still be successful.
>
> No packets would be sent in response to the RST segment, so the server should not retransmitt the
> (SYN,ACK) segment.
>
> There would be no timeout, as the server has received an RST segment and should close that
> connection immediately.

## Question 5
What effective window does Nagle authorize when in use for the first segment that is sent if nothing
is pending acknowledgment? When we study slow start and congestion avoidance, return here to
determine which massive traffic algorithm it resembles more: slow start (with what window (cwnd)
value?) or congestion avoidance?

> **Answer**
>
> The Nagle algorithm basically sets the effective window to 1 segment in this case, as only one
> outstanding small segment can be unacknowledged at at time. This is similar to the slow start
> algorithm, as in both cases the sender starts by sending one segment and waiting for ACK before
> proceeding.

## Question 6
What is WIN used for in a TCP connection? Is the parameter different for the receiver or the sender,
or does it have to be the same?

> **Answer**
>
> The effective window `WIN` or $V_{ef}$ limits the number of segments that can be be pending
> acknowledgement. It is the minimum value between the receiver window, which is the space in the
> receiver's buffer that is available, and the congestion window, which depends on the congestion
> control algorithm in use. The receiver and sender both have their own values for all of these
> parameters, independently of the other side's values.

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

> **Answer**
>
> RTO stands for "retransmission timeout". It is the timeout before an unacknowledged segment is
> retransmitted.
>
> The Jacobson algorithm only uses the Smooth RTT ($RTT_S$) in order to calculate the RTO.
>
> A good RTO estimate is necessary to avoid redundant rentransmission while also resending lost
> segments quickly. If it's too low, there could be retransmission of segments that arrived
> correctly if the ACK takes longer than expected to arrive. If it's too high, there may be wasted
> time waiting for an ACK that would never arrive.

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

> **Answer**
>
> When using fast recovery / fast retransmit, the congestion window and `ssthresh` are both set to
> half the `cwnd` value at time of receiving a triple duplicate ACK. The congestion control
> algorithm is then set to congestion avoidance mode.

## Question 12
About TCP windows

### Sub-question 12.a
What is the congestion window (cwnd)? When does its value change?

> **Answer**
>
> The congestion window `cwnd` is an estimate of how many segments can be sent and stay
> unacknowledged without risking losses due to congestion. Its value changes in 3 ways:
>
> 1. Upon receiving an ACK for a previously unacknowledged segment, `cwnd` grows. This growth
>    depends on the congestion control mode.
> 2. Upon receiving a triple duplicate ACK, `cwnd` shrinks to half its previous size.
> 3. Upon expiration of RTO, `cwnd` is reset to its starting size.

### Sub-question 12.b
What is the advertised window (WIN)? How do we find its value?

> **Answer**
>
> The advertised window `WIN`, also called the receiver window `rwnd`, is the amount of data that
> the receiver is willing to accept. Its value is sent in the header of every TCP segment, and is
> set to the amount of space left in the receiver's buffer. As the application consumes the data,
> the buffer is freed up, and the next TCP segment, whatever its content, will carry the updated
> window value. When data is received, it's placed in the buffer, and it stays there until the
> the application consumes it, filling up the buffer.

### Sub-question 12.c
What is the effective window? How is it calculated?

> **Answer**
>
> The effective window $V_{ef}$ is the minimum value between the congestion window, `cwnd`, and the
> advertised window, `rwnd`. It's the amount of data that a sender can send without getting
> acknowledgements. Once that amount of data is sent, the sender must wait. Upon receiving an ACK,
> `cwnd` is updated according to the congestion control algorithm, and `rwnd` is updated according
> to the value advertised in the ACK segment.

### Sub-question 12.d
What is the continuous sending window? How is it calculated?

> **Answer**
>
> The continuous sending window ($W_{cs}$) is the ideal value for the effective window. This value
> allows continuous transmission. A bigger window would have no effect on transmission speed, and a
> smaller window would enforce pauses. Its value can be calculated by dividing the RTT by $t_{tx}$,
> which is the time that it takes for a whole maximum-size segment to be sent. $W_{cs} =
> \frac{RTT}{t_{tx}}$. With this value, the effective window should be depleted just in time for an
> ACK to arrive.

### Sub-question 12.e
What is the relationship between the windows regarding the number of segments that can be sent per
RTT? (Indicate how each one influences the number of segments sent per RTT)

> **Answer**
>
> They both affect the number of segments that can be sent per RTT in the same way: they are a limit
> to that theoretical capacity. Whichever one has the lowest value is the limiting factor at that
> moment. If the limiting window is the `cwnd`, then once it grows, the amount of segments per RTT
> will increase. If the limiting window is the `rwnd`, then if it grows, the amount of segments per
> RTT will increase. In any case,, no matter how big both get, no more segments per RTT can be sent
> than the value of the continuous sending window, $\frac{RTT}{t_{tx}}$.

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
