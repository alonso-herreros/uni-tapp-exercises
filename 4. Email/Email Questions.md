## Telematic Applications <!-- omit in toc -->

# DNS Theory Questions •

*Academic year 2024-2025*

---

### Table of Contents

* [Question 1 •](#question-1-)
* [Question 2 •](#question-2-)
* [Question 3 •](#question-3-)
* [Question 4 •](#question-4-)
* [Question 5 •](#question-5-)
* [Question 6 •](#question-6-)
* [Question 7 •](#question-7-)
* [Question 8 •](#question-8-)
* [Question 9 •](#question-9-)
* [Question 10 •](#question-10-)
* [Question 11 •](#question-11-)
* [Question 12 •](#question-12-)
* [Question 13 •](#question-13-)
* [Question 14 •](#question-14-)
* [Question 15 •](#question-15-)
* [Question 16 •](#question-16-)
* [Question 17 •](#question-17-)
* [Question 18 •](#question-18-)

---

## Question 1 •
Does the email format with or without MIME need to indicate the total size of the
email?

> **Answer**
>
> No. Never.

## Question 2 •
A MIME email message composed of text in English and a JPG image, what headers
should it contain?

> **Answer**
>
> It requires the following headers:
>
> * `MIME-Version`
> * `Content-Type` with value `multipart/mixed` or `multipart/parallel`
> * In the english part:
>     * `Content-Type: text/*` where * is probably `plain`.
> * In the image:
>     * `Content-Type: image/*` where * could be one of many image formats.
>     * `Content-Transfer-Encoding: base64`

## Question 3 •
List the correct SMTP commands that you know:

> **Answer**
>
> The main commands needed to send an email are:
>
> * `HELO` / `EHLO`
> * `MAIL FROM`
> * `RCPT TO`
> * `DATA`
>
> Other commands we know are:
>
> * `QUIT`
> * `RSET`
> * `VRFY`
> * `EXPN`
> * `NOOP`

## Question 4 •
If an intermediate SMTP relay receives an email where the MAIL FROM field indicates a different address from the From field in the email format (RFC822), what
would happen?

> **Answer**
>
> The recipient specified `MAIL FROM` will receive the email as if the sender
> specified in the `From` header.

## Question 5 •
If an intermediate SMTP relay receives an email where the DATE field indicates a
date older than 30 days:

> **Answer**
>
> The date makes no difference, as `MTAs` should never *interpret* headers (they
> can only optionally *add* headers)

## Question 6 •
What is the first SMTP command that the client must send after opening a TCP
connection with the SMTP server on the corresponding port? Should the client
receive anything before proceeding with the first command?

> **Answer**
>
> The command is either `HELO` or `EHLO`. The client should wait for the server's
> welcome message before sending any other command.

## Question 7 •
What happens if the TCP connection over which POP3 is used between a client
and a server breaks? Are the changes finalized? What needs to happen before the
connection is closed or broken for the changes to take effect?

> **Answer**
>
> No changes are executed in the server, because the message `QUIT` was never sent
> by the client. The client should send a `QUIT` message

## Question 8 •
What type of identifiers does POP3 use (unique/absolute or relative)? What problems can this cause during the session? What practical issue would it have concerning
concurrent use?

> **Answer**
>
> Relative numbers. This can cause race conditions.

## Question 9 •
Can multiple commands be sent in parallel during a POP3 session?

> **Answer**
>
> No.

## Question 10 •
Does POP3 provide any security to prevent the user’s password from being compromised? How could this be addressed?

> **Answer**
>
> Yes. If the sender sends a nonce with its welcome message, with the `APOP`
> command, the user can authenticate by sending the hash of the password plus the
> nonce.

## Question 11 •
Does IMAPv4 allow the sending of multiple commands simultaneously? Always, at
any time? How does it distinguish responses if multiple commands are sent at once?

> **Answer**
>
> Yes. Every command is identified by a user-specified label, which is then
> included in the response

## Question 12 •
What do we call IMAP responses that start with *? What are they used for? What
happens with commands that allow multiple results (such as those that allow searching) if they are executed in parallel?

> **Answer**
>
> They are called **server data**: this is data about the operations performed by
> the server.
>
> If you run multiple parallel searches, all the results may arrive together and
> intermixed, which can be confusing.

## Question 13 •
In IMAPv4, in which state can searching be performed?

> **Answer**
>
> Searches can only be performed in the *SELECTED* state

## Question 14 •
List commands that can be used in any state of IMAPv4.

> **Answer**
>
> `CAPABILITY` and `NOOP` are the only commands that can be executed in any state.  

## Question 15 •
What are the possible results of the LOGIN command in the IMAP protocol? Are
the results... different from those of other commands?

> **Answer**
>
> The results of the `LOGIN` command are different: for all other commands, they
> can `OK`, `NO`, or `BAD`. For `LOGIN` it can only be `OK` or `BAD`.

## Question 16 •
Assuming two simultaneous IMAP sessions of the same user from different client
machines, and in one of them a message is marked with the delete flag, would that
delete flag be visible from the other session? Is it necessary to close the connection
or do something for it to happen?

> **Answer**
>
> The delete flag would be visible from t*he other session. It isn't necessary to
> close the connection or apply any other command in order to see the changes.

## Question 17 •
In IMAP4, there are two types of responses from a server, the “server data” type
and the “server completion result” type. How many of each can/should there
be? How do they differ?

> **Answer**
>
> There can be multiple *server data* messages in response to a single command
> (zero or more).
>
> There must be one and only one *server completion result* in response to a
> single command.

## Question 18 •
List the advantages of IMAP over POP concerning: use of multiple devices,
simultaneous commands, access to email and its parts.

> **Answer**
>
> In IMAP, multiple devices can be connected to the same mailbox at the same time
> and see the changes made by the other devices, while in POP3, the changes are
> only visible to the device that made them until they are committed and
> downloaded by the other devices.
>
> In IMAP, the client can send simultaneous commands and the server can process
> them in parallel, while in POP3, the client can only send one command at a time.
>
> In IMAP, the email contents are pre-processed by the server and presented to the
> client. It also supports complex searches and filtering. In POP3, the client
> downloads the email contents and processes them locally.
