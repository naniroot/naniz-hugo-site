---
title: "System Design Algorithm and Interview Cheat Sheet"
date: 2020-12-26T17:58:02-08:00
draft: false
images:
tags: [interviews, system design, coding, algorithms]
---

### References
1. [Leetcode post](https://leetcode.com/discuss/interview-question/system-design/547669/algorithm-you-should-know-before-system-design/526120)
2. [Github Source](https://github.com/resumejob/system-design-algorithms)

## Steps to System Design Interview 
1. Clarify Requirements
...* Ask lots of questions
...* Very important step, clarify requirements.
...* Spend good amount of time on this step
2. Adjust scope and state assumptions
...* Can limit scope to simplify and explain that you will come back to it at a later time
3. Back of the envelope calculations
...* This should set upper bounds on the high level design
4. High Level Design
...* Do drawings at this time
...* Keep it high level and explain trade offs
...* There is no one right answer. 
...* Stay in scope but try to leave room for future scale and features
5. Detailed Design
...* Discuss failure scenarios, how redundancy is provided, bottle necks, 
...* Discuss prevention of issues like thundering herd, hotspots, single point of failures etc
...* Focus on security as well in this step

## Algorithms and their Usage 

### Bloom filter
A Bloom filter is a data structure designed to tell you, rapidly and memory-efficiently, whether an element is present in a set.

- [Build a Web Crawler](http://blog.gainlo.co/index.php/2016/06/29/build-web-crawler/)

### Consistent Hashing
It is used to evenly divide work among a bunch of resources while giving flexibility for resources to be added or removed. Mostly used in database sharding.

- [Hash Ring](https://www.acodersjourney.com/system-design-interview-consistent-hashing/)

### Geohash / S2 Geometry
Geohash can be used by 1) dating apps to find romantic matches within a particular cell, and to create chat apps.2) Find nearby locations, and identify places of interest, restaurants, shops and accommodation establishments in an area. 3) Geohashers go on global expeditions to meet people and explore new places.

- [Location-based search results with DynamoDB and Geohash](https://read.acloud.guru/location-based-search-results-with-dynamodb-and-geohash-267727e5d54f)

### Leaky bucket / Token bucket
A mechanism to control the amount and the rate of the traffic sent to the network

- [Everything You Need To Know About API Rate Limiting](https://nordicapis.com/everything-you-need-to-know-about-api-rate-limiting/)
- [How to Design a Scalable Rate Limiting Algorithm](https://konghq.com/blog/how-to-design-a-scalable-rate-limiting-algorithm/)
- [How we built rate limiting capable of scaling to millions of domains](https://blog.cloudflare.com/counting-things-a-lot-of-different-things/)
- [Rate-limiting strategies and techniques](https://cloud.google.com/solutions/rate-limiting-strategies-techniques)

### Lossy Counting
The lossy count algorithm is an algorithm to identify elements in a data stream whose frequency count exceeds a user-given threshold.

- [Fast and Reliable Ranking in Datastore](https://cloud.google.com/datastore/docs/articles/fast-and-reliable-ranking-in-datastore)
- [Frequency Counts over Data Streams](https://www.cse.ust.hk/vldb2002/VLDB2002-proceedings/slides/S10P03slides.pdf)

### Operational transformation
Operational transformation (OT) is a technology for supporting a range of collaboration functionalities in advanced collaborative software systems.

- [How Google docs handle editing collisions](https://stackoverflow.com/a/36366174)
- [Operational Transformation Collaborative editing](https://en.wikipedia.org/wiki/Operational_transformation)

### Quadtree / Rtree
- [Spatial Indexing with Quadtrees](https://medium.com/@waleoyediran/spatial-indexing-with-quadtrees-b998ae49336)
- Find nearby interest points

### Ray casting
Ray casting is the most basic of many computer graphics rendering algorithms that use the geometric algorithm of ray tracing. Given a point with longitude and latitude, return the Country of the point.

- [Ray Casting Algorithm](http://philliplemons.com/posts/ray-casting-algorithm)

### Reverse index
Reverse Index: a reverse index is an index of keywords which stores records of documents that contain the keywords in the list.

- [How search engines work: Crawling, Indexing and Ranking](https://moz.com/beginners-guide-to-seo/how-search-engines-operate)
- [Building a complete Tweet index](https://blog.twitter.com/engineering/en_us/a/2014/building-a-complete-tweet-index.html)

### Rsync algorithm
The rsync algorithm is a technique for reducing the cost of a file transfer by avoiding the transfer of blocks that are already at the destination.

- [Streaming File Synchronization](https://dropbox.tech/infrastructure/streaming-file-synchronization)

### Trie algorithm
Trie is an efficient information reTrieval data structure. Using Trie, search complexities can be brought to optimal limit (key length)

- [How to Design an Autocomplete System](https://dzone.com/articles/how-to-design-a-autocomplete-system)
- [prefix matching words (IP Addresses, Phone Numbers)](https://www.geeksforgeeks.org/longest-common-prefix-using-trie/)
- [Auto-complete feature using Trie](https://www.geeksforgeeks.org/auto-complete-feature-using-trie/)

### Frugal Streaming
Frugal Streaming uses only one unit of memory per group to compute a quantile for each group

- Find the nth percentile of the data stream

### Count-Min Sketch
Count frequency in a stream of data. Approximate algorithm similar to bloom filter.

- [Approximate counts with Hashing](https://florian.github.io/count-min-sketch/)

### Least Recently Used (LRU)

### B-Trees

### Merkle Tree

## Honorable Mentions
- [HyperLogLog Algorithm for Cardinality Estimation](https://florian.github.io/count-min-sketch/)
- [Skip list to search a sorted linked list faster than O(n)](https://www.geeksforgeeks.org/skip-list/)
- [Hashed and Hierarchical Timing Wheels: Data Structures for the Efficient Implementation of a Timer Facility](https://blog.acolyer.org/2015/11/23/hashed-and-hierarchical-timing-wheels/)
- [Fenwick Tree](https://www.geeksforgeeks.org/binary-indexed-tree-or-fenwick-tree-2/)
