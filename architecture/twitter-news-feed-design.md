# News Feed Design ( Twitter )

Design an application which handles reading the news and posting the news in the timeline ( like twitter ) so that all the consumers / followers gets latest
news published from the user. Example use cases like,
- Twitter news feed 
- Instagram news feed 
- Facebook news feed 

# Steps 

## 1. Clarify Requirments 
- Not designing Twitter 
- Focusing on the NEWS feed part 
- Example: Twitter News Feed, FB news feed 

## 2. Clarify Things to Do ( Functional Requirment )
- Should be able to POST tweet / news  ( post tweet )
- All followers should get latest NEWS feed from the followie ( home timeline )
- Tweet / News feed has size limit ( upto certain char length )
- Tweet / News feed can post images, videos 
- Tweet / News feed should be in chronological order ( order in which the tweets are made )
- No re-tweet / or reposting 
- Add paginations and limit 50 feed per page 


## 3. Assumptions ( Non Functional Requirment )
- Scale with number of users/tweets 
- High availability ( 99.99% which will have around 50 minutes/year allowed downtime )
- Chronological Order in the news feed / tweet 
- Fault tolerant 

## 4. Challenges / Scenarios  
- Assuming 10k tweet posts/sec at peak hour needed to be added in timeline
- 
