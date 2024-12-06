### **4. Software and Application Limits**

This group focuses on the constraints and considerations within software development, particularly HTTP protocols, cookies, local storage, and other application-specific aspects.

---

#### **Key Topics and Answers**

---

#### **4.1 Maximum HTTP Header Size**
- **What is the maximum size of HTTP headers?**
  - The HTTP protocol itself doesn’t impose limits, but web servers and proxies set practical limits:
    - **Apache**: Default is **8KB** (`LimitRequestFieldSize` directive).
    - **Nginx**: Default is **4KB**, configurable up to **64KB**.
    - **IIS**: Default is **16KB** for both request and response headers.

- **What happens when header size exceeds the limit?**
  - The server returns an HTTP **413 Request Entity Too Large** or **431 Request Header Fields Too Large** response.

---

#### **4.2 Cookie Size and Count Limits**
- **What is the size limit for cookies?**
  - Most browsers limit the size of individual cookies to **4KB** (including name, value, and attributes).

- **What is the maximum number of cookies per domain?**
  - Typically **50 cookies** per domain, but some browsers (e.g., Chrome) allow up to **180 cookies** if total size doesn’t exceed **4KB per cookie**.

- **What happens when these limits are exceeded?**
  - Older cookies are evicted to make room for new ones.

---

#### **4.3 Local Storage and Session Storage Limits**
- **What are the size limits for local storage and session storage?**
  - Most browsers provide **5MB** of storage per origin (domain).
  - Storage limits can vary for different browsers:
    - **Chrome**: 10MB per origin.
    - **Safari/Firefox/Edge**: 5MB per origin.

- **What are the best practices for using local/session storage?**
  - Avoid storing sensitive data (e.g., passwords, JWTs).
  - Compress data before storing to save space.

---

#### **4.4 Maximum URL Length**
- **What is the maximum length of a URL?**
  - **IE**: 2,083 characters.
  - **Chrome/Firefox/Edge**: 32,768 characters (practical limits are much lower for usability).

- **What happens when the URL length exceeds limits?**
  - The browser will either truncate the URL or fail to load the resource.

---

#### **4.5 JavaScript Execution Time**
- **Is there a limit on JavaScript execution time?**
  - Browsers enforce a maximum execution time to prevent unresponsive scripts:
    - Typical timeout: **10 seconds**.
    - Long-running scripts trigger a "Stop running this script?" alert.

- **How to avoid long-running scripts?**
  - Use **Web Workers** for background processing.
  - Break large computations into smaller chunks.

---

#### **4.6 Rendering Constraints**
- **What are the limits on DOM node count?**
  - Browsers like Chrome can handle up to **1-2 million DOM nodes** before performance degrades significantly.
  - Rendering large DOM trees can lead to slow page load times and high memory usage.

- **How can rendering be optimized?**
  - Use **virtual DOM** (e.g., React).
  - Avoid unnecessary DOM nesting.
  - Use lazy loading for heavy elements.

---

#### **4.7 Maximum Simultaneous Connections**
- **How many simultaneous connections can a browser make?**
  - Modern browsers limit the number of simultaneous connections to a single domain:
    - **Chrome/Edge/Firefox**: 6 connections per domain.
    - **Safari**: 4 connections per domain.

- **How to optimize for connection limits?**
  - Use **HTTP/2**, which multiplexes multiple requests over a single connection.
  - Minimize the number of assets (e.g., combine CSS/JS files).

---

Would you like to explore a specific subtopic further or move to the next group?