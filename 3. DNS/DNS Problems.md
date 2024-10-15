## Telematic Applications

# TCP Problems

*Academic year 2024-2025*
*Dr. Daniel Díaz Sánchez*

---

## 1

Name, TTL, length, etc.

## 2

| Record type | Exists? |
| ----------- | ------- |
| ANY         | Yes     |
| NS          | Yes     |
| CFNAME      | Yes     |
| PTR         | Yes     |
| MXEX        | No      |
| HINFO       | Yes     |
| A           | Yes     |
| AXFR        | Yes     |
| HELO        | No      |
| PTR         | Yes     |

## 3

A PTR record

## 4

The TTL of the cached data in the (non-authoritative) server that sent the response.

## 5

The TTL advertised by the authoritative server, which is the maximum amount of time the record
**should** stay in anyone's cache. This is decided by the administrator(s) of the authoritative
server.

## 6

We should request the PTR to the reversed ip with `.in-addr.arpa` appended. The format is unusual
due to the fact that we have to write the more general part of the IP at the end.

In case of IPv6, the address is expanded, reversed and concatenated with `.ip6.arpa`

## 7

It has been sent through UDP, due to the fact that the `truncated` flag is set, indicating the
full response was not able to fit in the packet.

Primary or secondary server, since they have set the `authoritative answer` flag

## 8

Nothing, it's accepted.

TCP uses more resourced. Both are valid. UDP is used most of the time due to being more lightweight, but TCP is used when the whole data won't fit in UDP

## 9

The server is not required to give any type of answer, and can give an iterative answer to a request
with recursion desired. If servers were forced to recurse every time they were asked for it, they
would not be able to server all clients, which are a huge lot.
