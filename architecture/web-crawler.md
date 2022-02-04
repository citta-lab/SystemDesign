# Design Web Crawler 

Application which crawlers the internet for data to give the best results to user when they search for something. Example: Google, Bing, DuckDuckGo search engines do web crawling. Example use cases are like 

- Search Engine 
- Web Malware Detection 
- Copyright violation detection 
- Web analytics 
- Datascience 

# Steps : 

## 1. Clarify Requirments 
- HTTP ( are we supporting HTTP or/and HTTPS )
- HTML ( are we crawling just HTML ? maybe extend to other media types like video, images etc )

## 2. Clarify Things to do 
- Crawl Rate ( how often we will need to query other websites like CNN, HBO etc )
- Politeness ( shouldn't bombard with parallel crawls and obey allowed crawls interval  )
- In house DNS Query ( helps avoid querying DNS every time rather use hosted DNS query resolver )
- Priority/Weighted Crawling ( ranking )
- Distrubuted Crawling 
- Cycle Detection ( handle self referenced sites while crawling )
- Duplicate Detection ( avoid crawling same content or same site )

## 3. Assumptions  
- 1.18 billion registed websites (1,180,000,000)
- 17% are active websites i.e 200 million 
- Assuming 100 pages per site, will give us 2 billion pages to crawel 
- Assuming average size of a page is around 100KB 
- Storage number would be 2 petabit ( 2 billion * 100 kb )
- Minimum storage needed around 1 petabit if we use zip on content ( on top of 2.006e+12 )

## 4. Things to consider 
- Scalability ( to handle huge storage )
- Extensibility ( support other media types )
- Freshness ( how oftern we need to crawl. ex: news vs hotel menu )
- Server side rendering ( to crawl SPA's )
- Politness & Acknowledgment ( how often to crawl and pointing them the boat we use )

## 5. Architecture 






### 5.1 Seed URLS 
Prepare top 10 or 100 or 500 sites for each category like sports, technology, fashion, food etc. This will act as our reference and will need to keep this updated. 

### 5.2 URL frontier 
In this we focus on crawl rate, priority, piolitness assocaited with crawling. We will use QUEUE data structure to manage these aspects.

### 5.2 Fetcher + Renderer 
In this section we fetch the data/content associated with the each URL which is fed from "URL Frontier". We will work with THREADS ( go routines can have millions of routines to handle the crawling concurrently ). If the content is HTML then fetcher is used and if it's a SPA then we will do Server side rendering using NextJS to build complete SPA before crawling. 

we can scale horizontally just adding more machines based on demand.

Requests URL from URL frontier to crawl, does DNS lookup ( helps ) and does fetch or renderer using a thread. 

### 5.3 Storage 
Once the content is fetched or rendered we will need to save them in storage as meta-data. These meta-data will be big in size so we can ZIP and store in persistant storage however other process might need the fetched data for processing so we will keep the current UN ZIPPED data in redis for quick access. 

### 5.4 Response Queue 
Fetcher can store the data and add a message in the RESPONSE QUEUE which lets other services to pick up from the REDIS for futher processing. This can be used by URL extractor and Duplication Detection. 

### 5.5 Duplicate Detection 
Avoids recrawling something already crawled  

### 5.6 URL extractor 
Normalizes the URL to same case, add any missing HTTP protocols. Apply BFS or DFS way of processing all the child links in the page.

### 5.7 URL Loader 
Determines if the web page is already been crawled but this will be O(N) operation but we have around 600 million urls so we can use better algorithm to do the job in greedy way. Example: Bloom filter can be used and by passing multiple rounds of evaluation we can achieve the desired result. 

URL loader can also create blobs based on the domain so all sub domains will sit in one domain. etc for other domains. 



