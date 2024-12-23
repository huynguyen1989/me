---
title: HENNGE Assignment For Front-End Developer
description: Job's position assignment.
author: HUYNGUYEN	
date: 2024-04-07 12:12:00 +0800
categories: [Assignments]
tags: [Assignments, ReactJS, VueJS, NodeJS]
pin: false
math: true
mermaid: true
image:
  path: /assets/posts/2024/POST-ID-3/HENNGE_Logo.png
  alt: HENNGE one company logo.
---

<!-- POST-ID-4 -->
# A Developer's Challenge

The challenge is requires to develop a utility component that's based on VueJS and NodeJS development environment. So let's take a look through the given assets

<!-- Requirement -->
![Desktop View](/assets/posts/2024/POST-ID-4/FE_Job.png){: width="972" height="389" }


## Mission 1: Implement UI elements

The given challenge detailes: <https://huynguyen1989.github.io/me/assets/posts/2024/POST-ID-4/FE-HENNGE_Admission_Challenge.pdf> 

```text
Development of an Email Audit system is currently in progress. Assume that this project is a real
project and is being used in a production environment on a trial basis, since the features are not yet
complete.
You are tasked with implementing two UI elements to intelligently show email recipients in the
AuditTable component.
Inside the resource provided below, you will find a challenge
_
details folder and folders for the
different frameworks. The framework folders are identical projects implemented in their respective
framework.
You may choose any one of the frameworks to implement the RecipientsDisplay component. The
requirements are specified in CHALLENGE.md inside the challenge
_
. Please note
that you are not allowed to modify any other file (including adding new packages) to complete this
mission.
```

- So I chosed VueJS as the Solution

<!-- Requirement -->

- Given component prototype requirements

![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Email trim example 1.svg){: width="972" height="189"}
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Email trim example 2A.svg){: width="972" height="189"}
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Email trim example 2B.svg){: width="972" height="189"}
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Email trim example 3A.svg){: width="972" height="189"}
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Email trim example 3B.svg){: width="972" height="189"}
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Tooltip example 1.png){: width="972" height="189"}
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Tooltip example 2.png){: width="972" height="189"}

- Media view
![Desktop View](/assets/posts/2024/POST-ID-4/challenge/challenge_details/Evaluation.png){: width="972" height="289" }

## Mission 2: Publish your source code as a secret gist
> The implementation is considering as done due to the privacy of the assignment
{: .prompt-info }


## Mission 3: Send us the URL of your work

- Header of the example request
```text
  POST /challenges/004 HTTP/1.1
  Authorization: Basic bmluamFAZXhhbXBsZS5jb206SEVOTkdFQ0hBTExFTkdF
  Host: api.challenge.hennge.com
  Accept: */*
  Content-Type: application/json
  Content-Length: 136
  {"contact email":"ninja@example.com","github url":"https://gist.github.com/hennge/b8"}
```
- For the userid of HTTP Basic Authentication, use the same email address you put in the JSON string

- For the password , provide a string ASCII value " HENNGECHALLENGE " (not including double quotations)

- Body of the example request:
```json
{
  "contact email": "EMAIL",
  "github url": "https://gist.github.com/YOURACCOUNT/GIST ID",
  "solution framework": "FRAMEWORK"
}
```

So here's the gap of the challenge that I have to generate a request following there's guide and the authentication of the request based on `RFC2617` for header field `Authorization` 

## RFC2617 standard HTTP Authentication


- Here is a swim lane diagram of the MD5 hash calculation process in the context of `RFC2617`'s Digest Authentication:

```mermaid
 sequenceDiagram
        Client->>Server: Client GET /index
        Server->>Client: 401 Unauthorized WWW-Authenticate: basic realm="localhost"
        Client->>Server: Client calulate paramters MD5(A1_hash : nonce : nc : cnonce : qop : A2_hash)
        Client->>Server: Client sends response to server (Authorization header with username, realm, nonce, nc, cnonce, qop, response)
        Server->>Client: Server verifies response by recalculating hash and comparing to client's response
        Server->>Client: Server grants access if response is valid
```

- According to `RFC2617`, the following formulas are used to calculate the MD5 hash values:
```text
**A1**

`A1 = MD5(username : realm : password)`

Where:

* `username` is the username of the client
* `realm` is the authentication realm provided by the server
* `password` is the password of the client

**A2**

`A2 = MD5(HTTP-method : request-URI)`

Where:

* `HTTP-method` is the HTTP method used in the request (e.g., GET, POST)
* `request-URI` is the requested URI

**Response**

`response = MD5(MD5(A1) : nonce : nc : cnonce : qop : MD5(A2))`

Where:

* `MD5(A1)` is the result of the A1 calculation
* `nonce` is the nonce value provided by the server
* `nc` is the nonce count, a hexadecimal value that increments with each request
* `cnonce` is the client nonce, a random string generated by the client
* `qop` is the quality of protection, which determines the level of security used for the authentication process
* `MD5(A2)` is the result of the A2 calculation

**Note**: The `:` character is used to represent concatenation.

**Digest Response**

The final response sent by the client to the server is in the following format:

`Digest username="username", realm="realm", nonce="nonce", nc="nc", cnonce="cnonce", qop="qop", response="response"`

Where:

* `username` is the username of the client
* `realm` is the authentication realm provided by the server
* `nonce` is the nonce value provided by the server
* `nc` is the nonce count
* `cnonce` is the client nonce
* `qop` is the quality of protection
* `response` is the result of the response calculation
```
## Finallize

- After many attempts and drafts, the crafted response below matches the `RFC2617` standard

```text
  curl -v -X POST  \
   -H "Content-Type: application/json" \
   -H "Authorization: Basic b2NoZW5mdXNpb25AcHJvdG9uLm1lOkhFTk5HRUNIQUxMRU5HRQ==" \
   -H "Accept: */*" \
   -H "Host: api.challenge.hennge.com" \
   --data '{"github_url":"https://gist.github.com/huynguyen1989/7a19321116244636c4448c3cdaec4c3a","contact_email":"ochenfusion@proton.me","solution_framework":"vue"}' \
    https://api.challenge.hennge.com/challenges/004
```

- API Responses

```text
  https://api.challenge.hennge.com/challenges/003 POST
  +---------------HttpResponse----------------------+
  {"message":"Congratulations! You have achieved mission 3"}

  +---------------HttpResponse----------------------+
  {"message":"Could not save your solution. It is possible that the applicant does not exist or their solution has been already provided. Please check your input."}
```

- And finally, you will get an email from HENNGE. 

![Desktop View](/assets/posts/2024/POST-ID-4/email_response.png){: width="972" height="389" }
