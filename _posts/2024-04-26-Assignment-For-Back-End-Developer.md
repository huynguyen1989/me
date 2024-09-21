---
title: HENNGE Assignment For Back-End Developer
description: Job's position assignment.
author: HUYNGUYEN	
date: 2024-04-07 12:12:00 +0800
categories: [Assignments]
tags: [Assignments, Golang, Python, NodeJS]
pin: false
math: true
mermaid: true
image:
  path: /assets/posts/2024/POST-ID-3/HENNGE_Logo.png
  alt: HENNGE one company logo.
---
<!-- POST-ID-5 -->

# A Developer's Challenge

The challenge is requires to develop a program that's based on Golang environment. So let's take a look through the given assets

<!-- Requirement -->
![Desktop View](/assets/posts/2024/POST-ID-5/BE_Job.png){: width="972" height="589" }

## Mission 1: Write a program which fulfills the requirements below

The given challenge detailes: <https://huynguyen1989.github.io/me/assets/posts/2024/POST-ID-5/BE-HENNGE_Admission_Challenge.pdf> 

```text
- Description
We want you to calculate the sum of squares of given integers, excluding any negatives.
The first line of the input will be an integer N ( 1 <= N <= 100 ), indicating the number of test
cases to follow.
Each of the test cases will consist of a line with an integer X ( 0 < X <= 100 ), followed by
another line consisting of X number of space-separated integers Yn (-100 <= Yn <= 100 ).
For each test case, calculate the sum of squares of the integers, excluding any negatives, and
print the calculated sum in the output.
Note: There should be no output until all the input has been received.
Note 2: Do not put blank lines between test cases solutions.
Note 3: Take input from standard input, and output to standard output.

- Rules
Write your solution using Go Programming Language or Python Programming Language. Do not
submit your solution with both languages at once!
You may only use standard library packages. In addition, extra point is awarded if solution does not
declare any global variables.

- Specific rules for Go solution
Your source code must be a single file
Do not use any for and goto statement
Your solution will be tested against Go 1.20 (as of February 2023) or higher
package main
func main() {
...
}

- Specific rules for Python solution
Your source code must be a single file, containing at least a main function
Do not use any for loop, while loop, or any list / set / dictionary comprehension
Your solution will be tested against Python 3.11 (as of February 2023) or higher
  def main():
  ...
    if __name__ == "__main__":
  main()
```

> I can only share the implementation of unit-test only due to the privacy of the challenge
{: .prompt-info }

- Following the Notes of the requirements so the test cases would be:
1. Test happy path input params: 
```text
    input := "2 4 6 8 10 99\n"
    expectedOutput := "10021"
    func -> TestInputHappyPathWithAllPositiveNumberAndNoFloat
```
2. Test input all positive integer including float numbers: 
```text
    input := "2 .4 6.6 88\n"
    expectedOutput := "7791.72"
    func -> TestInputAllPositiveNumbers
```
3. Test input negative, positive, float
```text
    input := "11 22.22 .3333 66.66 -1 -.2 -0.3 -6\n"
    expectedOutput := "5058.4"
    func -> TestInputSidedNegativePositiveNumbers
```

```go
package main

import (
    "os"
    "testing"
    "fmt"
)
// Each of the test cases will consist of a line with an integer X  ( 0 < X <= 100 ), 
// followed by another line consisting of X  number of space-separated integers Yn  ( -100 <= Yn <= 100 ). 

// For each test case, calculate the sum of squares of the integers, excluding any negatives, 
// and print the calculated sum in the output. 

// Note 2: Do not put blank lines between test cases solutions.
func TestInputHappyPathWithAllPositiveNumberAndNoFloat(t *testing.T) {
    input := "2 4 6 8 10 99\n"
    expectedOutput := "10021"

    oldStdin := os.Stdin
    r, w, _ := os.Pipe()
    os.Stdin = r

    w.Write([]byte(input))
    w.Close()

    rescueStdout := os.Stdout
    r, w, _ = os.Pipe()
    os.Stdout = w

    main()

    os.Stdout = rescueStdout
    w.Close()

    outC := make(chan string)
    go func() {
        var buf [1024]byte
        n, _ := r.Read(buf[:])
        outC <- string(buf[:n])
    }()

    os.Stdin = oldStdin

    actualOutput := <-outC


    if actualOutput != expectedOutput {
        t.Errorf("Expected output %q, but got %q", expectedOutput, actualOutput)
    }
    fmt.Println(actualOutput)
}
func TestInputAllPositiveNumbers(t *testing.T) {
    input := "2 .4 6.6 88\n"
    expectedOutput := "7791.72"

    oldStdin := os.Stdin
    r, w, _ := os.Pipe()
    os.Stdin = r

    w.Write([]byte(input))
    w.Close()

    rescueStdout := os.Stdout
    r, w, _ = os.Pipe()
    os.Stdout = w

    main()

    os.Stdout = rescueStdout
    w.Close()

    outC := make(chan string)
    go func() {
        var buf [1024]byte
        n, _ := r.Read(buf[:])
        outC <- string(buf[:n])
    }()

    os.Stdin = oldStdin

    actualOutput := <-outC
    if actualOutput != expectedOutput {
        t.Errorf("Expected output %q, but got %q", expectedOutput, actualOutput)
    }
    fmt.Println(actualOutput)
}
func TestInputSidedNegativePositiveNumbers(t *testing.T) {
    input := "11 22.22 .3333 66.66 -1 -.2 -0.3 -6\n"
    expectedOutput := "5058.4"

    oldStdin := os.Stdin
    r, w, _ := os.Pipe()
    os.Stdin = r

    w.Write([]byte(input))
    w.Close()

    rescueStdout := os.Stdout
    r, w, _ = os.Pipe()
    os.Stdout = w

    main()

    os.Stdout = rescueStdout
    w.Close()

    outC := make(chan string)
    go func() {
        var buf [1024]byte
        n, _ := r.Read(buf[:])
        outC <- string(buf[:n])
    }()

    os.Stdin = oldStdin

    actualOutput := <-outC
    if actualOutput != expectedOutput {
        t.Errorf("Expected output %q, but got %q", expectedOutput, actualOutput)
    }
    fmt.Println(actualOutput)
}
func TestInputNestedNegativePositiveNumbers(t *testing.T) {
    input := "11 -1 22.22 -.2 .3333 -0.3 66.66 -6\n"
    expectedOutput := "5058.4"

    oldStdin := os.Stdin
    r, w, _ := os.Pipe()
    os.Stdin = r

    w.Write([]byte(input))
    w.Close()

    rescueStdout := os.Stdout
    r, w, _ = os.Pipe()
    os.Stdout = w

    main()

    os.Stdout = rescueStdout
    w.Close()

    outC := make(chan string)
    go func() {
        var buf [1024]byte
        n, _ := r.Read(buf[:])
        outC <- string(buf[:n])
    }()

    os.Stdin = oldStdin

    actualOutput := <-outC
    if actualOutput != expectedOutput {
        t.Errorf("Expected output %q, but got %q", expectedOutput, actualOutput)
    }
    fmt.Println(actualOutput)
}

```


## Mission 2: Publish your source code as a secret gist
> The implementation is considering as done due to the privacy of the assignment
{: .prompt-info }

## Mission 3: Send us the URL of your work
```text
- Authorization
The URL is protected by HTTP Basic Authentication, which is explained on Chapter 2 of RFC2617, so
you have to provide an Authorization: header field in your POST request
For the userid of HTTP Basic Authentication, use the same email address you put in the JSON
string.
For the password , provide a 10-digit time-based one time password conforming to RFC6238
TOTP.
- Authorization password
For generating the TOTP password, you will need to use the following setup:
You have to read RFC6238 (and the errata too!) and get a correct one time password by
yourself.
TOTP's Time Step X is 30 seconds. T0 is 0.
Use HMAC-SHA-512 for the hash function, instead of the default HMAC-SHA-1 .
Token shared secret is the userid followed by ASCII string value " HENNGECHALLENGE003 " (not
including double quotations).
Shared secret examples
For example, if the userid is "ninja@example.com"
, the token shared secret is
"ninja@example.comHENNGECHALLENGE003"
.
For example, if the userid is "ninjasamuraisumotorishogun@example.com"
, the token shared
secret is "ninjasamuraisumotorishogun@example.comHENNGECHALLENGE003"
If your POST request succeeds, the server returns HTTP status code 200 .
- Rules
You do not have to disclose how you achieved this mission at this time. Do not hesitate to use
source codes or tools on the net, but do the exploring process by yourself of course, do not ask
your friend to help you. The only thing that matters is that it works!
No bruteforce attacks, please!
```

- So in the FE job position challenge I have deal with `RFC2617` and this mission is requiring the knowledge of both `RFC2617` and `RFC6238`,
 `Authorization password` is generated by TOTP from `RFC6238` 

 - Given parameters
 1. The sample request from assignment is using `HTTP/1.1`  
 2. `You have to read RFC6238 (and the errata too!) and get a correct one time password by yourself.`
 3. `TOTP's Time Step X is 30 seconds. T0 is 0`.
    Use `HMAC-SHA-512` for the hash function, instead of the default `HMAC-SHA-1` .
    Token shared secret is the userid followed by `ASCII` string value `HENNGECHALLENGE003`
 4. For example, if the userid is `"ninjasamuraisumotorishogun@example.com"`, the token shared secret is `"ninjasamuraisumotorishogun@example.comHENNGECHALLENGE003"`


```text
POST /challenges/004 HTTP/1.1
  Authorization: Basic bmluamFAZXhhbXBsZS5jb206SEVOTkdFQ0hBTExFTkdF
  Host: api.challenge.hennge.com
  Accept: */*
  Content-Type: application/json
  Content-Length: 136
{
  "github url": "https://gist.github.com/YOURACCOUNT/GISTID",
  "contact email": "EMAIL",
  "solution language": "golang"
}
```


### Notes to solve challenges

- I was attempts generate the request with some libraries with many stars from github but they keeps getting 

```json
{
     "message": "Access denied: Invalid token, malformed token"
}
```

- I took a deep dive into many libraries from various languages, including Python, Java, C/C++, and Golang, to implement the standards and read the core of the implementation. However, I didn't select any of them. Specifically, in algorithm implementation, the core base would use different libraries in the `Compiler Layers`, which would make our generated `SHA521` and `TOTP` slightly different between them.

- Let's read about the Compiler of the given standards `RFC2617` and `RFC6238` 

> For details of `RFC2617`: <https://www.rfc-editor.org/rfc/rfc2617>
{: .prompt-info }
> For details of `RFC2638`: <https://www.rfc-editor.org/rfc/rfc6238>
{: .prompt-info }

### SHA512

 Here are some key things to know about SHA512:

- SHA512 is a cryptographic hash function that maps data of arbitrary size to a 512-bit digest. It is part of the SHA-2 family of hashes.

- The output is a 512-bit (64 byte) hexadecimal string that represents the input data. SHA512 generates a unique hash for even slightly different inputs.

- It is a one-way function, meaning the input data cannot be derived from the hash. It can only be used to verify that data matches a known hash.

- SHA512 is considered collision resistant, which means it is infeasible to find two inputs that produce the same hash. This makes it suitable for applications like file integrity checking. 

- It is also preimage resistant, so given a hash, it is infeasible to find the input data that produces it. This makes it suitable for password storage.

- Common uses of SHA512 include file integrity verification, password storage, digital signatures, blockchain applications, and other places cryptographic hashes are needed.

- To generate a SHA512 hash, you pass the input data to a SHA512 hashing algorithm implementation. Popular tools include OpenSSL, sha512sum, and cryptographic libraries in languages like Python and JavaScript. 

- The hash can be compared byte-for-byte to the expected hash to verify the input data has not changed.

So in summary, SHA512 is a cryptographically secure one-way hash function that maps arbitrary data to a 512-bit hash value, making it suitable for integrity checks and password storage where collision and preimage resistance are important properties.

 Here is a more mathematical description of the SHA512 hash algorithm:

- SHA512 operates on blocks of 1024 bits (128 bytes) at a time. The input message is padded to be evenly divisible by 1024 bits then processed in successive 1024-bit blocks.

- Each block is broken into sixteen 128-bit words denoted M0, M1, ..., M15. These words act as the initial hash state.

- The hash state is represented as eight 64-bit words denoted a, b, c, d, e, f, g, h. 

- The hash state is initialized to the following fixed constants:

  a = 0x6a09e667f3bcc908

  b = 0xbb67ae8584caa73b

  c = 0x3c6ef372fe94f82b

  d = 0xa54ff53a5f1d36f1

  e = 0x510e527fade682d1

  f = 0x9b05688c2b3e6c1f

  g = 0x1f83d9abfb41bd6b

  h = 0x5be0cd19137e2179

- The input words M0-M15 are processed using 80 rounds of SHA512's compression function. Each round applies modular addition, bitwise logic and substitution tables to update the hash state.

- After 80 rounds, the final hash state (a, b, c, d, e, f, g, h) represents the 512-bit hash of that 1024-bit block.

- The process repeats for each subsequent block, with the previous hash state used as the initial state for the next block.

- The final hash value after all blocks is the concatenation of the final a, b, c, d, e, f, g, h values.

So in summary, SHA512 applies modular arithmetic and bitwise logic operations over multiple rounds to compress an input into a fixed-length 512-bit hash value.

### TOTP RFC6238

 Here is a more mathematical description of TOTP (Time-based One-Time Password) as defined in RFC 6238:

- TOTP generates one-time passwords based on a shared secret key and the current time period. It produces a new password at fixed time intervals (usually 30 seconds).

- The secret key is a base32-encoded byte string agreed upon between the client and server during initial setup. 

- The current time period is the number of time steps that have elapsed since the Unix epoch (January 1, 1970 00:00:00 UTC), divided by the time step interval (usually 30 seconds). 

- This time period is converted to an integer by truncating any fractional part. This gives the time step t.

- The secret key and time step t are hashed together using the HMAC-SHA-1 algorithm:

  HMAC(key, t)

- The output of the HMAC is a 160-bit string. Only the first n bits (usually the first 6 decimal digits) are extracted, where n is the number of digits in the OTP. 

- This extracted n-bit string is the one-time password (OTP) for that time period.

- When authenticating, the client calculates the OTP for the current time period t and sends it to the server. 

- The server independently calculates the expected OTP using the same shared secret and time period t to verify the response.

So in summary, TOTP combines a shared secret key with the current time period using HMAC-SHA1 to randomly but deterministically generate one-time passwords at fixed intervals for multi-factor authentication.

## Final
- For my userid and shared secret is: `huynguyen1989@proton.meENNGECHALLENGE003`

- For the SHA512 generate I was use openssl to generate `SHA521` manually with bash

```bash
  echo -n "huynguyen1989@proton.meENNGECHALLENGE003" | openssl dgst -sha512 -d
```
- 10-digit time-based one time password conforming to `RFC6238` `TOTP`
- `TOTP` Shared secret is `huynguyen1989@proton.meENNGECHALLENGE003`
- `TOTP` hash Algorithm is `HMAC-SHA-512`
- About the parameters of `TOTP`, It's not required my machine's timestamp to match with server's timestamp. So With the post request `TOTP` The server could:
  1. Check to verify the given password
  2. Check my time spent when resolving the challenge
  3. Check my generated `TOTP` would match the standard or not ( belive me you won't getting successful without reading all the TOTPT erra like they said `You have to read RFC6238 (and the errata too!) and get a correct one time password by
yourself.`)
 

- I posted my console dump when resolving the challenge that may useful for you to solve the challenge

```text
/Home/bin/java -javaagent:/Applications/IntelliJ IDEA.app/Contents/lib/idea_rt.jar=57731:/Applications/IntelliJ IDEA.app/Contents/bin -Dfile.encoding=UTF-8 -Dsun.stdout.encoding=UTF-8 -Dsun.stderr.encoding=UTF-8 -classpath /IdeaProjects/TOTP/out/production/TOTP Main
+---------------+Time millis----------------------+
1712450702<< TIME MILLIS
57081690<< TIME STEPS
+---------------+steps----------------------+
000000000366FF5A
+---------------+T----------------------+
57081690
HmacSHA512<<Input crypto<<
10<<Input codeDigits<<
000000000366FF5A<<Input time<<
000000000366FF5A<<time<<
[B@3af49f1c<<key hexStr2Bytes(key)<<
[B@19469ea2<<k byte[]<<
[104, 117, 121, 110, 103, 117, 121, 101, 110, 49, 57, 56, 57, 64, 112, 114, 111, 116, 111, 110, 46, 109, 101, 72, 69, 78, 78, 71, 69, 67, 72, 65, 76, 76, 69, 78, 71, 69, 48, 48, 51]<<k byte[] to Arrays.toString(k)<<
huynguyen1989@proton.meHENNGECHALLENGE003<<new String(byteArray, StandardCharsets.UTF_8)<<
307040704<<binary<<
307040704<<otp<<
307040704<<result<<
0307040704<<< RESULT SHA512
+---------------Base64----------------------+
huynguyen1989@proton.me:0307040704
+---------------Encoded----------------------+
aHV5bmd1eWVuMTk4OUBwcm90b24ubWU6MDMwNzA0MDcwNA==
+---------------Decoded----------------------+
huynguyen1989@proton.me:0307040704
+---------------Http Request----------------------+
+---------------Encode header----------------------+
aHV5bmd1eWVuMTk4OUBwcm90b24ubWU6MDMwNzA0MDcwNA==
https://api.challenge.hennge.com/challenges/003 POST
+---------------HttpResponse----------------------+
{"message":"Congratulations! You have achieved mission 3"}

Process finished with exit code 0

----------------------------------------------------------------------------------------------------------------------------------

/Home/bin/java -javaagent:/Applications/IntelliJ IDEA.app/Contents/lib/idea_rt.jar=57966:/Applications/IntelliJ IDEA.app/Contents/bin -Dfile.encoding=UTF-8 -Dsun.stdout.encoding=UTF-8 -Dsun.stderr.encoding=UTF-8 -classpath /IdeaProjects/TOTP/out/production/TOTP Main
+---------------+Time millis----------------------+
1712451362<< TIME MILLIS
57081712<< TIME STEPS
+---------------+steps----------------------+
000000000366FF70
+---------------+T----------------------+
57081712
HmacSHA512<<Input crypto<<
10<<Input codeDigits<<
000000000366FF70<<Input time<<
000000000366FF70<<time<<
[B@3af49f1c<<key hexStr2Bytes(key)<<
[B@19469ea2<<k byte[]<<
[104, 117, 121, 110, 103, 117, 121, 101, 110, 49, 57, 56, 57, 64, 112, 114, 111, 116, 111, 110, 46, 109, 101, 72, 69, 78, 78, 71, 69, 67, 72, 65, 76, 76, 69, 78, 71, 69, 48, 48, 51]<<k byte[] to Arrays.toString(k)<<
huynguyen1989@proton.meHENNGECHALLENGE003<<new String(byteArray, StandardCharsets.UTF_8)<<
791180043<<binary<<
791180043<<otp<<
791180043<<result<<
0791180043<<< RESULT SHA512
+---------------Base64----------------------+
huynguyen1989@proton.me:0791180043
+---------------Encoded----------------------+
aHV5bmd1eWVuMTk4OUBwcm90b24ubWU6MDc5MTE4MDA0Mw==
+---------------Decoded----------------------+
huynguyen1989@proton.me:0791180043
+---------------Http Request----------------------+
+---------------Encode header----------------------+
aHV5bmd1eWVuMTk4OUBwcm90b24ubWU6MDc5MTE4MDA0Mw==
https://api.challenge.hennge.com/challenges/003 POST
+---------------HttpResponse----------------------+
{"message":"Could not save your solution. It is possible that the applicant does not exist or their solution has been already provided. Please check your input."}

Process finished with exit code 0

```

### Result

> After getting the successful request I received an email response to upload my CV
{: .prompt-info }

![Desktop View](/assets/posts/2024/POST-ID-5/email_response.png){: width="972" height="589" }

