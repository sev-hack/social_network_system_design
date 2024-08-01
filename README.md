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
- max number of characters in a post - 1 000
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
