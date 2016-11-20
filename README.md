# Twitter System Design

![twitter image](https://abs.twimg.com/icons/apple-touch-icon-192x192.png)

## System Design Challenge

“Design a simplified version of Twitter where people can post tweets, follow other people and favorite tweets.”

## Clarifying Questions

If you're working through this problem by yourself or doing a mock interview with a friend, these are the answers that the interviewer would give to the following questions:

*Q: How many users do we expect this system to handle?*
*A: You can expect to have 10 million users generating 100 million requests per day.*

*Q: How many other users will the average person be following?*
*A: We expect that each user will be following 200 other users on average, but expect some extraordinary users with tens of thousands of followers.*

*Q: How many new tweets and new favorites can we expect each day?*
*A: We expect that there will be a maximum of 10 million tweets per day and each tweet will probably be favorited twice on average but again, expect some big outliers.*

## Resources

Abbreviations that I'll use in the solution:
  * B - billion (e.g. 10B = 10 billion)
  * M - million
  * GB - gigabyte (e.g. 10 GB = 10 gigabytes)
  * TB - terabyte


## The Solution

### Step 1: Contraints and Use Cases

#### Use Cases

The first thing that we'll need to do is clarify the use cases.  It's also helpful to note which use cases are read operations and which use cases are write operations.

* Posting new tweets (write)
* Following a user (write)
* Favoriting a tweet (write)
* Displaying data about users and tweets (read)

Next we'll describe how the user will interact with the application so that we know you and the interviewer are on the same page. For example, there will be a profile page for each user, which will show us their latest tweets and will allow for older tweets to be shown. Each such page will have a button for following the user. There will also be a button at the top of the page, which will allow logged in users to open a dialog box and write a message in it. After they click a button the message will be stored and will appear on their profile page. 

#### Constraints

We need to ask some clarifying questions in order to nail down our constraints.

*Q: How many users do we expect this system to handle?*
*A: You can expect to have 10 million users generating 100 million requests per day.*

*Q: How many other users will the average person be following?*
*A: We expect that each user will be following 200 other users on average, but expect some extraordinary users with tens of thousands of followers.*

*Q: How many new tweets and new favorites can we expect each day?*
*A: We expect that there will be a maximum of 10 million tweets per day and each tweet will probably be favorited twice on average but again, expect some big outliers.*

To summarize:
  * 10M users
  * 10M tweets per day
  * 20M tweet favorites per day
  * 100M requests per day
  * 2B “follow” relations (10M tweets * 200 followers/following = 2B edges)
  * Some users and tweets could generate an extraordinary amount of traffic

##### Load
100M total requests/day => 1150 req/second

10M tweets/day => 115 tweets/second
20M favorites/day = > 230 favorites/second

This traffic will be distributed unevenly throughout the day so the system should be able to handle at least a few thousand requests per second.

##### Data

Storing the tweets:

10M tweets/day => 3.65 tweets/year
Let's aim for a solution that can efficiently store 10B tweets
Let's assume that each tweet will be 140 characters.
1 char = 1 byte 
10B tweets * 140 bytes/tweet = 1.4 TB  

Storing the "follow" relations:

2B follow relations
Each relation will contain two user ids (the follower and the followee)
Let's make each user id 4 bytes, so each follow relation will be 8 bytes
8 bytes * 2B = 16B bytes = 16 GB


Storing the favorites: 

20M favorites/day => 7.3B favorites/year
Let's aim for a solution that can efficiently store 20B favorites
A favorite will consists of a user id and a tweet id
User ids are 4 bytes each
Tweet ids are 8 bytes each
Each favorite will be 12 bytes
12 bytes * 20B = 240B bytes = 240 GB

Total storage capacity = 1.4 TB + 16 GB + 240 GB = ~2.7 TB

### Step 2: Abstract Design


### Step 3: Bottlenecks

  
### Step 4: Technology Decisions 


### Step 5: Scaling
