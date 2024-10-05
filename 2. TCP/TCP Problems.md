# TCP Exercises

## 1. Basic Problems

### Problem 1

Let the TCP connection configured with a MT U = 1320 Bytes, running over a
20Mbps link with a propagation time of 5ms. Calculate the RTT (Round Trip Time)

> **Answer** ($✓$)
>
> First, we'll find the transmission time for the biggest segment possible, $T_{txSEG}$. This is a
> transmission of maximum size, so its size (including headers) is the MTU: $1320$ bytes
>
> $$
> T_{tx} = \frac{S_{tx}}{R_{tx}} = \frac{1320 · 8}{20 · 10^6} = 528 \text{ μs}
> $$
>
> Then, we'll find the transmission time for an ACK segment, $T_{txACK}$. This only includes the IP
> and TCP headers, so its size is $40$ bytes
>
> $$
> T_{txACK} = \frac{S_{tx}}{R_{tx}} = \frac{40 · 8}{20 · 10^6} = 16 \text{ μs}
> $$
>
> With this, the RTT is:
>
> $$
> RTT = T_{txSEG} + T_{txACK} + 2T_{prop} = 0.528 + 0.016 + 2 · 5 = 10.544 \text{ ms}
> $$
