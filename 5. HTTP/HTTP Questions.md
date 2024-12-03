## Telematic Applications <!-- omit in toc -->

# HTTP Theory Questions

*Academic year 2024-2025*

---

### Table of Contents

* [Question 1](#question-1)
* [Question 2 •](#question-2-)
* [Question 3 ✓](#question-3-)
* [Question 4 •](#question-4-)
* [Question 5 ✓](#question-5-)
* [Question 6 •](#question-6-)
* [Question 7 ✓](#question-7-)
* [Question 8 ✓](#question-8-)
* [Question 9](#question-9)
* [Question 10 ✓](#question-10-)
* [Question 11 ✓](#question-11-)
* [Question 12 ✓](#question-12-)
* [Question 13 ✓](#question-13-)
* [Question 14 ✓](#question-14-)
* [Question 15](#question-15)
* [Question 16 ✓](#question-16-)
* [Question 17 ✓](#question-17-)

---

## Question 1
What are entity, general and request headers? What type of header is the header
`From`?

## Question 2 •
What HTTP authentication mechanisms do you know? Explain the characteristics
of each one.

> **Answer**
>
> The HTTP authentication mechanisms we know are `Basic` and `Digest`.

## Question 3 ✓
In the HTTP protocol, what type of information does the `Date` header provide,
and what is its primary function?

> **Answer**
>
> The `Date` header contains a timestamp. It serves as a timestamp for the
> request or response. It is not mandatory.

## Question 4 •
In HTTP/1.1, if a client makes a GET request for a web page that does not exist
on the server, what type of response does the server send? Explain the meaning
of this response.

> **Answer**
>
> The server sends a `404 Not Found` response. This means that the server cannot
> find the requested resource.

## Question 5 ✓
In HTTP/1.0, what method is used in the request line to request a document from
the server? What information does this line contain?

> **Answer**
>
> The method is `GET`. The request line contains:
>
> * The method `GET`
> * The URI `<document>`
> * The protocol version `HTTP/1.0`
>
> ```http
> GET <document> HTTP/1.0
> ```

## Question 6 •
Explain the main improvements introduced by HTTP/1.1 compared to HTTP/1.0.

> **Answer**
>
> HTTP/1.1 added more headers, methods, presistent connections, proxy and cache

## Question 7 ✓
In HTTP/1.1, what type of information does the `Content-Description` header
carry? In what requests is it useful?

> **Answer**
>
> The `Content-Description` header doesn't exist.

## Question 8 ✓
What does the Host header allow in HTTP/1.1? Why is it mandatory in this version
of the protocol?

> **Answer**
>
> The `Host` header allows the server to know which domain the client is trying
> to access. It is mandatory in HTTP/1.1 because it allows the server to host
> multiple domains on the same IP address.

## Question 9
In HTTP/1.1, what is chunked encoding, and what is its primary purpose? Provide
an example of its use.

> **Answer**
>
> Chunked encoding is a way of sending data in chunks instead of all at once.
> Its purpose is to fragment the data into smaller pieces if it's too large.
> The size is sent in hexadecimal format before the data, and a 0 indicates the
> end of the data.

## Question 10 ✓
In an HTTP POST request for HTTP/1.0 or HTTP/1.1, what header(s) are mandatory?

> **Answer**
>
> The mandatory headers for HTTP/1.0 and HTTP/1.1 are:
>
> * `Host`
> * `Content-Length`

## Question 11 ✓
How does HTTP implement state management? Explain the mechanisms the protocol
uses for this purpose.

> **Answer**
>
> HTTP is a stateless protocol, but to manage states it uses cookies using the
> `Set-Cookie` and `Cookie` headers.

## Question 12 ✓
What is the function of the `Connection: Close` header in an HTTP/1.1 request?

> **Answer**
>
> It states the client's intention to close the connection after the request is
> completed, as in HTTP/1.1 the connections are persistent by default. It can
> also be sent by the server.

## Question 13 ✓
In HTTP/1.1, what is the purpose of the Referer header? Provide an example.

> **Answer**
>
> The `Referer` header is used to indicate the URL of the previous page from
> which the client navigated to the current page. It is useful for tracking
> where the client is coming from, but it is not mandatory in any case.
>
> For example, if a user clicks on a link on a website, the `Referer` header
> will contain the URL of the website where the user clicked the link.

## Question 14 ✓
What are the differences between the HTTP methods PUT and POST? Provide
examples of situations where each method would be most appropriate.

> **Answer**
>
> The `PUT` method is used to update a resource, while the `POST` method is used
> to create a new resource. For example, if you want to update a user's
> information, you would use the `PUT` method. If you want to create a new user,
> you would use the `POST` method.

## Question 15
In HTTP/1.1, explain how content negotiation works and what headers are used for
this purpose.

## Question 16 ✓
In HTTP/2, what is the purpose of having the Server Push functionality enabled?,
how does this affect a client request? Explain the process and its impact on
protocol performance.

> **Answer**
>
> The **Server Push** functionality allows the server to send resources to the
> client before the client requests them by anticipating the client's needs.
> It uses a `PUSH_PROMISE` frame to send the resource to the client.
>
> This is negotiated using the `SETTINGS_ENABLE_PUSH` setting.

## Question 17 ✓
What are the main improvements introduced by HTTP/3 compared to HTTP/2?

> **Answer**
>
> HTTP/3 uses QUIC instead of TCP, allowing for all of the benefits of QUIC
> such as faster connection establishment, improved congestion control, and
> better security.
