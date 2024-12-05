### **1. Network and Data Transfer: Detailed Answers**

#### **1.1 Network Payload Limits**
- **What is the maximum payload size for HTTP requests and responses?**
  - Typically, there’s no hard limit set by the HTTP protocol itself, but practical limits are imposed by web servers:
    - **Apache HTTP Server**: Default is 2MB for requests (`LimitRequestBody` directive).
    - **Nginx**: Default is 1MB for client request bodies (`client_max_body_size` directive).
    - **AWS API Gateway**: 10MB for requests and responses.
    - **Browsers**: Generally handle responses up to 2GB.

- **How do limits differ for GET vs. POST requests?**
  - **GET requests**: The URL length (including query parameters) has practical limits:
    - **IE**: ~2,048 characters.
    - **Chrome, Firefox, Edge**: ~65,000 characters.
  - **POST requests**: Limits depend on the server’s configuration (e.g., 2MB in Apache or Nginx by default).

---

#### **1.2 API Request Size**
- **What are the maximum size limits for RESTful and GraphQL APIs?**
  - RESTful APIs: Typically limited by server configuration or API Gateway limits (e.g., AWS API Gateway = 10MB).
  - GraphQL APIs: Same limits as RESTful APIs, though splitting large queries into smaller ones is advised for better performance.

- **How does the request size impact latency and throughput?**
  - Larger requests take more time to upload and process, increasing latency.
  - High payload sizes can choke network bandwidth, reducing throughput for other requests.

- **Best practices to handle large payloads:**
  - Use **pagination** for large data sets.
  - Implement **file uploads** via multipart/form-data.
  - Compress requests and responses (e.g., using Gzip).

---

#### **1.3 WebSocket Message Limits**
- **What is the maximum message size for WebSocket communication?**
  - Typically, **65,536 bytes (64 KB)** is the limit for a single message on most implementations, but this can vary:
    - Node.js `ws` library: Default is 100 MB.
    - Browsers: Varies but usually large enough for most use cases.

- **How can you handle fragmented WebSocket messages?**
  - Use **message framing** where large messages are split into fragments.
  - Ensure the server and client support continuation frames for reassembly.

---

#### **1.4 Browser Upload/Download Limits**
- **Maximum upload/download sizes supported by browsers:**
  - Browsers themselves don’t impose hard limits, but OS and server configurations do:
    - Single uploads can go up to **4GB** on modern browsers.
    - Download size is limited by disk storage or file system constraints.

- **How do browsers handle file chunks for large uploads?**
  - Large uploads are handled via **chunked encoding** or multipart upload mechanisms (e.g., AWS S3 multipart upload).

---

#### **1.5 Timeouts and Retries**
- **Typical timeout values for HTTP requests:**
  - **Browsers**: 30-120 seconds (depends on browser settings).
  - **Axios**: Default is no timeout, but you can configure it (e.g., `timeout: 5000` for 5 seconds).
  - **AWS Lambda/API Gateway**: 29 seconds max for synchronous calls.

- **Retries:**
  - Implement exponential backoff for retries (e.g., retry after 1s, 2s, 4s).
  - Limit retries to **3-5 attempts** to avoid overwhelming the server.

---

#### **1.6 Streaming Data**
- **Limits for real-time data streaming:**
  - **HTTP/2**: No theoretical limit but practical limits exist (e.g., TCP congestion).
  - **WebRTC**: Typically, 500 KBps for video/audio streams.

- **Best practices for live streaming:**
  - Use adaptive bitrate streaming protocols (e.g., DASH, HLS).
  - Ensure buffer size and network latency are managed for low-latency streaming.

---

#### **1.7 CORS and Preflight Requests**
- **CORS Limitations:**
  - Preflight requests can fail due to server configuration or exceeding size limits.

- **How to reduce unnecessary preflight requests:**
  - Use **simple requests** that don’t trigger preflight checks (e.g., avoid custom headers like `Authorization` unless necessary).
  - Enable server caching for preflight responses using the `Access-Control-Max-Age` header.

---

#### **1.8 Mobile Network Constraints**
- **Challenges in low-bandwidth scenarios:**
  - Avoid large requests; compress payloads.
  - Use caching to reduce repetitive network calls.

---

#### **1.9 Proxy and Firewall Constraints**
- **Maximum size allowed by proxies:**
  - Common limits:
    - **Squid Proxy**: Default max object size is 4GB.
    - **Nginx Proxy**: Limits match backend server settings.

---

#### **1.10 CDN and Cache Constraints**
- **CDN Payload Size Limits:**
  - Cloudflare: Supports up to **500MB** for free plans.
  - AWS CloudFront: Object size limits up to **20GB**.

Would you like to dive deeper into any of these subtopics or move on to the next group?