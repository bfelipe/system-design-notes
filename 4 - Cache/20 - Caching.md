## Caching

Caching is a technique that allows us to copy a certain amount of data to operate read/write opperations faster than usually could happen if done on Memory Ram or Disk.

# The downside of caching

Besides Caching allowing such powerful feature, having copies of data in distributed datasources can lead to one of them get data outdated. Syncing mechanisms must be built to ensure consistency over time.

# The computer case

As we previously discussed in Computer Architecture, CPU allows us to cache data that can be quickly accessed during computation.
Although CPU cache presents limitations, since we often deal with huge amount of data, CPU cache can only handle kilobytes to megabytes.
CPU cache have three levels of cache, L1, L2, L3.

# L1 level

L1 level of CPU cache is the smallest and the fastest unit of caching in the CPU. It can't hold more than 128kb per CPU core.

# L2 level

L2 level is not as fast than L1 level cache, but it can store few more kilobytes per core, to just a few megabytes.

# L3 level

L3 level is the largest cache level, although the slowest of the three. It can share across CPU core about 32mb to 64mb.

# How cache is controlled and managed by CPU?

CPU implements policies of how cache is built from selected data from memory. Policies such as data cohelation, to data least recent used, to pattern of access in Memory Ram.

# The web broswer/client case

Everytime we access a web page, if caching is enabled in the brower, static content that is transfered over the network is stored in the disk.
This allow that future requests in that page, part of its content that doesn't have changed is quickly rendered for our final user.
Things like images, javascript code, html, css are examples of static content of a web page.
When another request is done for a web page which its content has been cache we use to say we got a **cache hit**, which means the content which we needed has been found. Otherwise we got a **cache miss**.
It is important to state that cache often has time to live, in other words it can be expired. So even when I have data that is stored in the disk due cache, but it is expired, this will lead to a cache misss.
Caching from the web browser perspective can be seen as uninportant, but imagine if each time a user hit a page, and there tons of static content is transfered to his browser. Future requests can make his experience pleasant since the time he gonna have to wait for the site to render will decrease. This has a term name, Cache Ratio.

# Cache Ratio

Cache ratio is refered to a percentage of cache hits over a cache misses.
As high the percentage of cache hits is, it means the cache done in the disk was efficient, which means, no new requests are needed to be made in the server to download the missing content, in other words overall performance of the application in the browser and better user experience.

The equation to measure Cache Ratio can be described as the follow:

    cache hit ratio % = (number of cache hits / total of requests) * 100

    ex

    cache hit ratio = 92% = (92/100) * 100

Since we got 92% of cache hit ratio, only 8% was considered cache miss, and will need extra network request.

# The server case

Caching in the server side can be tricky, because we can leverage from memory chaching based on different scenarios.
Which each scenario gives us a policy of how caching is going to be operated.
There are three different policies we can use cache in the server side

- write around
- write through
- write back

## Write around

This policy applies when have an intense writting flow which data is persisted direcly in the disk, since we don't have frequent reads.

## Write through

This policy applies when we want to ensure data concistency, do data is stored in the memory cache and the disk. Everytime the data is updated it is update on both sides, although it may increase write latency due to this sync operation.

## Write back

This last policy applies in a very specific scenario, where the data is first persisted in the memory cache, and once it gets full or reach a certain time to live we remove the data from memory and persist it into the disk.
This allow the system to continue certain operations without the wait of writing on the disk.
Although it may lead to data loss if the cache system goes down, so an extra system such as log or stream may be useful to recover what was missing.

## Eviction cache policies

When we talked about Write Back policy it was mentioned that the data is removed when the memory cache is full or reach a certain time to live (TTL), so open space for new data to be cached in the future.
Which we haven't spoke is about Eviction cache policies.
Each one behave in an unique way. There are three Eviction cache policies.

- First in First out (FIFO)
- Least Recently Used (LRU)
- Least Frequently Used (LFU)


## First in First out (FIFO)

It behaves like a queue data structure, where the first item to be added to the cache is the first to be removed when the memory cache if full.
This policy can be implemented using a TTL mechanism, so there is always certain the first item been cached is going to be the first to be expired and removed by the cache system.

## Least Recently Used (LRU)

The LRU policy removes an item when the memory cache reaches its limit, where the data itself haven't been accessed in a long time so the rate that it is gonna be read in the future is also low.
This policy can be implemented using three approaches.
The first is using a timestamp, which each time this data is used, the timestamp is update with the current time, old data will be easy to filter later and removed from the cache.
The second approach is to add an access count, each time the data is access this access count is increased, which allows you to see what data has the lowest access counts compared to the highest.
The last approach is to move the most recent data accessed to the beginning of the cache list, less often accessed data is certain to be those at the hear.

## Least Frequently Used (LFU)

Finally LFU is a policy that aims to remove data that is less frequently accessed, once the cache reaches its limits.
In real life, LFU is implemented using a hashmap data structure, which allows you to maintain the count of the most frequent accessed or writen data into the cache.
Some libraries allows you to do this sort of maintainance for all three Eviction cache policies.

But wait a minute, LFU and LRU seems pretty much the same.
Besides they may look similar at first and even can use similar data structures and operations to remove data, they differ on how they prioritize the Eviction of the data.

A cache using a LRU may look data to be removed which is per example 2 months old without access, in other words VERY OLD in terms of age.
While a cache using a LFU look data to be removed which is per example 1 week old without access, in other words just a few hours, days or weeks, so not soo old compared to data using LRU policy.
