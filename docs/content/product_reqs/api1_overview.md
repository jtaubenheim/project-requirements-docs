---
title: HyperCore API
tags: [api1]
toc: false
permalink: api1_overview.html
---

I wanna make some changes. 

In the creation of HCOS as a whole and specifically in the creation of the Scaled thrift API and REST API V1, many reasonable people made many reasonable assumptions about what **should** and **should not** work, what was **required** to work and what was **recommended** to work. Since it wasn't specified, those reasonable developers may have built on an assumption of an API based on how it was delivered.

## API Version 1 Thrift / REST

The current API version works in a reasonable way but provides little in the way of guaranteed behaviors. In the absence of a guarantee, an API consumer should probably assume that there is none. In the absence of a statement saying there is no guarantee, the API publisher has less standing to claim that API clients have relied on undefined behavior. While it can be argued that Scale could change undefined items in v1 behavior, it is probably in Scale's best interest to strive to keep v1 constant in areas that matter.
