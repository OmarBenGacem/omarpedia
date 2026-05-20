# Overview
Replica set pods are stateless and ephemeral, meaning they have no external memory (stateless), and they have no “identity” (ephemeral). An example of this is an API, because from query to query, API requests are all considered separate to each other[^1]. Similarly, replica sets are highly scalable (think 5 API calls coming in at the same time), and this is possible due to them being stateless. Similarly (all managed by Kubernetes), they are self-healing, which allows them to instantly be recreated should a node or pod fail.

  

---

[^1]: If this is difficult to understand, consider how most of the time, you do 2 requests: First you request a token, then you do a separate request for another token. Logically, if you already got a token when you asked, why do you then need to re-submit it with your next request? This is because APIs are stateless, meaning they don’t ‘remember’ that you already have a token.