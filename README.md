# Social Network - System Design

Example of the homework for [course by System Design](https://balun.courses/courses/system_design). Social Network is a special social network for travellers.

## Functional requirements:

- publishing travel posts with photos, a small description and a link to a specific travel destination
- rating and commenting on other travelers' posts
- subscribing to other travelers to follow their activity
- finding popular places to travel and viewing posts from those places
- viewing other travelers' feeds

## Non-functional requirements:

- 10 000 000 DAU
- geo distribution is not needed (only CIS countries)
- availability 99,95%
- seasonality (users travel often in summer)
- on average, each user creates 3 posts per week
- on average, each post contains 2 photos
- on average, each user leaves 5 comments per day
- on average, each user reacts 5 times per day
- on average, each user finds popular places 2 times per day
- on average, each user sends 10 request per day (feed update, read post)
- the feed has only the first photo from each post of followed travelers
- max photo size - 2 Mb
- max number of characters in a comment - 200
- max number of characters in a post - 1 000
- max number of characters in a "find popular places" request - 50
- max amount of subscribers per one user - 100 000
- post, reactions and comments are always stored
- timings:
  - no more than 2 seconds on publishing post
  - no more than 1 second on leaving comments and reactions
  - no more than 2 seconds on finding popular places
  - no more than 1 second on viewing feed and reading post

## Basic calculations

RPS (create post):
```
DAU = 10 000 000
Each user creates 3 posts per week
RPS = 10 000 000 * 3 / 86 400 / 7 = 50 
```

RPS (reactions):
```
DAU = 50 000 000
Each user reacts 5 times per day
RPS = 10 000 000 * 5 / 86 400 = 600 
```

RPS (leave comments):
```
DAU = 50 000 000
Each user leaves 5 comments per day
RPS = 10 000 000 * 5 / 86 400 = 600 
```

RPS (find popular places):
```
DAU = 50 000 000
Each user finds popular places 2 times per day
RPS = 10 000 000 * 2 / 86 400 = 250 
```

RPS (view feed and read post):
```
DAU = 50 000 000
Each user sends 10 request per day (feed update, read post)
RPS = 10 000 000 * 10 / 86 400 = 1200 
```

Traffic (create post):
```
Max photo size - 2 Mb (x2 photos in each post)
Max number of characters in a post - 1 000
Traffic = 50 * (2048 KB * 2 + 1000 B) = 205 MB/s
```

Traffic (reactions):
```
Meta info - 15 B
Traffic = 600 * 15 B = 9 KB/s
```

Traffic (leave comments):
```
Max number of characters in a comment - 200
Traffic = 600 * 200 B = 120 KB/s
```

Traffic (find popular places):
```
Max number of characters in a "find popular places" request - 50
Traffic = 250 * 50 B = 12,5 KB/s
```

Traffic (view feed and read post):
```
Max photo size - 2 Mb (only one photo)
Traffic = 1200 * 2048 KB = 2500 MB/s
```
