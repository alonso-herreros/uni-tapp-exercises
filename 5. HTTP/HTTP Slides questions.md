## Telematic Applications

# HTTP Slides questions

*Academic year 2024-2025*

* [Telematic Applications](#telematic-applications)
* [Slides Question 1](#slides-question-1)
* [Slides Question 2](#slides-question-2)
* [Slides Question 3](#slides-question-3)
* [Page 52 Question 1 ✓](#page-52-question-1-)
* [Page 52 Question 2 ✓](#page-52-question-2-)
* [Page 52 Question 3 ✓](#page-52-question-3-)

---

## Slides Question 1
There were no headers considered in the protocol

## Slides Question 2
There were no status or error return codes
Only `html` documents could be retrieved

## Slides Question 3
It consists of a request and a response.

## Page 52 Question 1 ✓

```http
GET /www/image1.png HTTP/1.1
Host: www.it.uc3m.es
Accept: image/png
```

## Page 52 Question 2 ✓

We can add the `Accept:` header to specify the type of content we want to
receive:

* To accept `GIF` images: `Accept: image/gif`
* To accept `JPEG` images: `Accept: image/jpeg`
* To accept `PNG` images: `Accept: image/png`
* To accept any of the above: `Accept: image/gif, image/jpeg, image/png`
* To accept any type of image: `Accept: image/*`

## Page 52 Question 3 ✓

```http
HTTP/1.1 200 OK
Date: <date>
Server: <server>
Content-Type: image/png
Content-Length: <length>
```
