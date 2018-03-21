---
layout:     post
title:      "Redis学习 - Redis Tutorial"
subtitle:   "Hello World for Redis"
date:       2018-03-21
author:     "Chie"
header-img: "img/in-post/redis-tutorial/post-bg-redis-tutorial.jpg"
tags:
    - 服务器开发
    - 数据库
    - Redis
---

![](/img/in-post/redis-tutorial/try-redis.png)  

# 前言  

算是写了两年的iOS，最近很任性地转去了服务器，从零开始。问了问leader需要学些什么，里面就包含Redis，于是就有了这篇拖延了两年的第一篇博文。

虽然此时的我对Redis一无所知，但是还是要鼓起勇气写下来，也算是给自己开个头，希望今后能够定期更新吧。

# Redis Tutorial

> Redis是一个使用ANSI C编写的开源、支持网络、基于内存、可选持久性的键值对存储数据库。

支持的数据类型包括strings，hashes（类似于obeject），lists（有序列），sets（无序集合），sorted sets（有序集合）。

## operations
* **SET** [key] [value]
* **SETNX** [key] [value] => set-if-not-exists
* **GET** [key]
* **DEL** [key]
* **INCR** [key] => automatically increment a number stored at key, is an atomic operation 
* **EXPIRE** [key] [seconds] => set a key should only exist for a certain length of time
* **TTL** [key] => check how long will a key exist, return -2 for not exist and return -1 for never expire

## list operations
* **RPUSH** [key] [value] => push the value at the end of the list if the key doesn't exist as a different type
* **LPUSH** [key] [value] => push the value at the start of the list
* **LRANGE** [key] [index] [index] => give a subset of the list, a value of -1 for the second parameter means to retrieve elements until the end of the list.
* **LLEN** [key] => return the current length of the list
* **RPOP** [key] => remove the last element from the list and return it

## set operation
* **SADD** [key] [value]
* **SREM** [key] [value]
* **SISMEMBER** [key] [value] => test the given value is in the set.return 1 if the value is there and 0 if it is not
* **SMEMBERS** [key] => return a list of all the members in set
* **SUION** [key1] [key2] .. => combine two or more set and return a list of all the mumbers

## sorted set operation
> A sorted set is similar to a regular set, but now each value has an associated score. This score is used to sort the elements in the set.

* **ZADD** [key] [score] [value] 
* **ZRANGE** [key] [index1] [index2]  

## hashes operation  
> Hashes are maps between string fields and string values, so they are the perfect data type to represent objects.

* **HSET** [key] [field] [value]  
* **HMSET** [key] [field1] [value1] [field1] [value2] .. => set multiple fields at once
* **HGETALL** [key]  
* **HGET** [key] [field]  
* **HINCRBY** [key] [field] [count] => atomically increment hash field, exatly the same as in simple strings
* **HDEL** [key] [field]

## more

Tutorial的最后是下面的四个链接可以更深入地学习

* [Redis Documentation](https://redis.io/documentation)
* [Command Reference](https://redis.io/commands)
* [Implement a Twitter Clone in Redis](https://redis.io/topics/twitter-clone)
* [Introduction to Redis Data Types](https://redis.io/topics/data-types-intro)
