### **7. Frontend/Backend Performance**

This group focuses on performance limits and optimization techniques for frontend rendering, backend processing, and JavaScript execution.

---

#### **Key Topics and Answers**

---

#### **7.1 Browser DOM Node Limits**
- **What are the limits on DOM node count?**
  - Modern browsers can handle **1-2 million DOM nodes**, but performance degrades with large DOM trees.
  - Practical limit for good performance: **10,000-50,000 DOM nodes**.

- **How can DOM size be optimized?**
  - Use **virtual DOM** frameworks (e.g., React, Vue).
  - Avoid unnecessary DOM elements or deep nesting.
  - Use **lazy loading** for heavy elements (e.g., images, videos).

---

#### **7.2 Rendering Constraints**
- **What are the limits for CSS and rendering performance?**
  - Maximum CSS selectors: Browsers support **4,096 selectors per stylesheet** (e.g., IE).
  - CSS file size: Keep under **1MB** for optimal load times.

- **How to optimize rendering performance?**
  - Use **minified CSS and JavaScript**.
  - Avoid large inline styles and redundant rules.
  - Reduce repaint and reflow by batching DOM updates.

---

#### **7.3 JavaScript Execution Time**
- **What are the practical limits on JavaScript execution?**
  - Long-running scripts (e.g., >10 seconds) trigger browser warnings.
  - Browsers may terminate scripts exceeding execution limits to prevent page freezing.

- **How to optimize JavaScript performance?**
  - Split large tasks using **setTimeout** or **requestAnimationFrame**.
  - Use **Web Workers** for background processing.
  - Minify and bundle JavaScript files.

---

#### **7.4 API Request Concurrency**
- **How many simultaneous requests can be made to a single domain?**
  - Modern browsers limit concurrent requests:
    - **6-8 requests** per domain for HTTP/1.1.
    - Unlimited requests for HTTP/2 (multiplexing supported).

- **How to optimize API requests?**
  - Use **HTTP/2** for better concurrency.
  - Batch multiple requests into a single API call.
  - Cache responses using client-side or server-side caching.

---

#### **7.5 Asset Loading Limits**
- **What are the limits for assets like images and fonts?**
  - Browsers typically support **up to 1,000 concurrent resources**, but performance drops after **50-100 assets**.
  - Individual asset size:
    - Images: Avoid exceeding **1-5MB**.
    - Fonts: Keep under **200KB** per font file.

- **How to optimize asset loading?**
  - Use **lazy loading** for images and videos.
  - Serve optimized formats like **WebP** for images.
  - Combine and minify assets to reduce HTTP requests.

---

#### **7.6 Backend Request Processing**
- **What are the constraints on backend request handling?**
  - Max request size:
    - REST APIs: Limited by server configuration (e.g., Nginx default: 1MB).
    - GraphQL APIs: Split large queries into fragments.

- **How to improve backend processing?**
  - Use **caching** for frequently requested data.
  - Optimize database queries with proper indexing.
  - Implement asynchronous processing for long-running tasks.

---

#### **7.7 Real-Time Data Handling**
- **What are the limits for real-time features like WebSockets?**
  - A single server can handle:
    - **10,000-100,000 WebSocket connections** depending on memory and CPU.
  - Message size limit:
    - Typically **64KB** per message, configurable in most libraries (e.g., `ws` in Node.js).

- **How to scale real-time applications?**
  - Use load balancers to distribute WebSocket connections.
  - Employ message brokers (e.g., Redis, RabbitMQ) for high-throughput communication.

---

Would you like to delve into a specific subtopic or move to the next group?