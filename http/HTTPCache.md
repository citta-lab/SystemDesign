# HTTP Cache ( Browser Cache ):
By default all browsers support HTTP Cache and which helps in improving the latency and performance of the consumer facing applications. These are all the main thing we should know,

## Main API's 
Below are the response headers will be added by the server for all it's outgoing responses.

#### Cache-Control 
Defines how and how long the is applied for outgoing responses.The following Cache-Control values can help you fine-tune where and how unversioned URLs are cached:

- `no-cache`. This instructs the browser that it must revalidate with the server every time before using a cached version of the URL. Often used for resources that should be revalidated with the server before every use.
- `no-store`. This instructs the browser and other intermediate caches (like CDNs) to never store any version of the file. Used for resources that should never be cached like `server status` etc.
- `private`. Browsers can cache the file but intermediate caches cannot.
- `public`. The response can be stored by any cache.

All the versioned resources we can set the maxiumum default value as 1 year expiration `Cache-Control: max-age=31536000`. If the resource is changed our hash/version will be different and our old cache will be evicted. However mutable files like `index.html` cannot be solved easily and will always have to relay on `no-cache` startegy unless we use `service worker` which refereshes in the background.

#### ETag
Acts as a token/hash to indicate if the resource has been changed or not. Server verifies this from the browser ( small in size ) and it it's not changed then server returns with `304-Not Modified` otherwise it will return the diff token.

#### Last-Modified 
Works similar to ETag but more of time based rather than content based.

## How to Improve
### Preperation:
Identify if the assests are `mutable` vs `immutable`. If they are `mutable` then can we version the assests / resources or use versioning directives to seperate them from old assest vs new. Example, `javascript` files, `css`, `html`. Build tool like `webpack` does this job better by adding a new hash after the name of the file to indicate the new version.
```js
- index.html
- app.js
- app.css
```
The naive way of version would be `app.v1.js` and `app.v1.css`. However we cannot simply use the versioning to `index.html` as it is the entry point to the app. This falls into Special case. In build tool such as webpack will append the hash like 
```js
- app.wew724kdfdsfnsdfds.js
- app.w2wewerkdfdsfnsdfds.css
```
If they are immutable ( example `png`, `jpeg`, `healthCheck.html` server status check ) then we can use them directly but having the version will help.





## Reference 
[HTTP Cache](https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching)
[Go Daddy](https://www.godaddy.com/engineering/2019/11/19/frontend-caching-quick-start/)
