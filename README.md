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

Let’s make a few very simple calculations with the information we just received. We will have around 10 million users. Average number of followed other users is 200. This means that the network of users will have about 200 * 10 million edges. This makes 2 billion edges. If the average number of tweets per day is 10 million the number of favorites will then be 20 million.

10 million users
10 million tweets per day
20 tweet favorites per day
100 million HTTP requests to the site
2 billion “follow” relations
Some users and tweets could generate an extraordinary amount of traffic

##### Load

##### Data

### Step 2: Abstract Design


### Step 3: Bottlenecks

  
### Step 4: Technology Decisions 


### Step 5: Scaling
