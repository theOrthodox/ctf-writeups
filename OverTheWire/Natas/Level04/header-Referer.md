# Header : Referer

## What is the Referer Header?

The **Referer header** is an **HTTP request header** that indicates the URL of the webpage from which the request originated. In simple terms, it tells the server **where the request came from**.

When a user clicks a link, loads an image, or submits a form, the browser may include the Referer header in the request to inform the server about the previous page that triggered the request.

Interestingly, the word **"Referer"** is misspelled in the official HTTP specification and has remained that way for historical reasons.

---

## Example

Suppose a user is visiting the following page:

```
https://example.com/page1
```

If the user clicks a link that leads to:

```
https://example.com/page2
```

The browser may send a request like this:

```
GET /page2 HTTP/1.1
Host: example.com
Referer: https://example.com/page1
```

In this case, the Referer header informs the server that the request for `page2` originated from `page1`.

---

## Common Uses of the Referer Header

### 1. Analytics and Traffic Tracking

Websites use the Referer header to analyze where visitors are coming from. This helps determine whether users arrived via search engines, social media, or external websites.

### 2. Security Checks

Some applications check the Referer header to verify that a request originates from their own website. This can help mitigate certain attacks such as **Cross-Site Request Forgery (CSRF)**, although it should not be relied upon as the only security measure.

### 3. Hotlink Protection

Web servers sometimes use the Referer header to prevent **hotlinking**, where other websites directly embed images or files hosted on another server.

### 4. Logging and Debugging

Servers may log Referer headers to understand user navigation patterns or troubleshoot issues.

---

## Limitations and Privacy Considerations

Although the Referer header is useful, it has several limitations:

* Browsers may **omit or modify** the header for privacy reasons.
* Security policies such as **Referrer-Policy** can restrict how much information is sent.
* HTTPS to HTTP requests may **remove the Referer header** entirely.
* Since the header can be **manually modified**, it should not be trusted for critical security decisions.

---

## Related Header: Referrer-Policy

The **Referrer-Policy** response header allows websites to control how much referrer information is included with requests. It helps protect user privacy by limiting the data shared between websites.

Example:

```
Referrer-Policy: no-referrer
```

This policy prevents the browser from sending the Referer header at all.

---


