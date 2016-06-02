---
layout:     post
title:      Estimation of Arbitrary Subset Sum with Priority Sampling
date:       2016-06-02
summary:    Silakan klik pada judul untuk detailnya
categories: tugas
---

#Estimation of abritary subset sum with priority sampling

Suppose we have a stream of object and each stream has a non-negative weighht, we want to maintain a generic sample of a certain limited size which can be use to estimate the total weight of arbitary subsets.
Many scheme to solve that problem has a disadvantage at controlling the size of the sample. 
<br>
A good way to solve that problem is use a cheme proposed by Duffield, Lund, and Thorup; called priority sampling.
<br>
*This article is base on Duffield, Lund and Thorup paper "Priority Sampling for Estimation of Arbitary Subset Sums".*

##Index
1. [Introduction](#introduction)
2. [Priority Sampling](#priority-sampling)
3. [References](#references)

##Introduction
This article is focus on sampling from a high volume stream of weighted items. The items arrive faster and in larger quantities than can be saved, so only a sample can be stored efficiently. We want to create a generic sample of a certain limitedsize that we can later use to estimate the total weight of arbitrary subsets. 
<br><br>
Applied to internet traffic analysis, the items could be records summarizing the flows of packets streaming by a router, with, say, a hundred records to be sampled each hour. A subset could be flow records of a worm attack whose signature is only determined after sampling has taken place. The samples taken in the past allow us to trace the history of the attack even though the worm was unknown at the time of sampling.

##Priority Sampling
Suppose we are give n items with weight w. The goal is to compute all the subset sum queries. In some situations, when n is huge, we can't really store all the weights from the item. The way to compute that is take a sample from the universe and then calculated the weight of the sample. 
<br><br>
There's many techniques to take a sample; from *randomly picked up sample* - missed item with high weight to *weighted sample* - always give high weight items. Each of the schemes show a vulnarablity but there is an elegant scheme proposed by Duffield, Lund, and Thorup which called priority sampling.
<br><br>
<img src="https://github.com/MalvinJu/MalvinJu.github.io/blob/MalvinJu-patch-1/1.PNG">
<br>
Image1. Priority sampling of size 3 from a set of 10 weighted item
<br><br>
The priority sampling scheme as can seen bellow :
* For each item, generate a random number a<sub>i</sub> between 0 and 1. Assign a priority  <sub>i</sub> to i of value w<sub>i</sub>/a<sub>i</sub> where q<sub>i</sub> is unique from others.
* S is the set of items with the k highest prorities.
* Take the top k elements (with respect to priority), and let the priority of the (k+1)<sup>th</sup> element be t. If k >= n set t = 0.
* If i is subset of S, set w<sup>'</sup><sub>i</sub> = max(w<sub>i</sub>, t), else set w<sup>'</sup><sub>i</sub> = 0.


##References
* Nick Duffield, Carsten Lund, and Mikkel Thorup. Priority sampling for estimation of arbitrary subset sums. Journal of the ACM (JACM), 2007.
