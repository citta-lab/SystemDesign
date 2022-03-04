# HTTP 1.1 vs HTTP 2
In HTTP1.1, data sent over HTTP protocal are one at a time and server waits for the acknoledgement before sends next set of data.

HTTP 2 has detailed control over prioritization. This allows them to maximize perceived and actual page load speed to a degree that was not possible in HTTP/1.1. HTTP/2 offers a feature called weighted prioritization. This allows developers to decide which page resources will load first, every time.

This method of data delivery is known as multiplexing. Developers can assign each of these data streams a different weighted value, and the value tells the client which data stream to render first.

- Multiplexing : HTTP/2 is able to use a single TCP connection to send multiple streams of data at once so that no one resource blocks any other resource. HTTP/2 does this by splitting data into binary-code messages and numbering these messages so that the client knows which stream each binary message belongs to.

- Server push: HTTP/2 solves this problem by allowing a server to "push" content to a client before the client asks for it. 

- Header Compression : HTTP/2 uses a more advanced compression method called HPACK that eliminates redundant information in HTTP header packets. This eliminates a few bytes from every HTTP packet.

## How can developers improve web performance ?
- Use CDN
- Optimized images
- Minify CSS and Js file
- Reduce number of HTTP requests
- Min number of external scrips 
- Avoid using redirects 