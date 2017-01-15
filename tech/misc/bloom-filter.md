_15/01/2017_

## Bloom Filter

A Bloom filter is a space-efficient probabilistic data structure that is used to test whether an element is a member of a set. False positive matches are possible, but false negatives are not. In other words, a query returns either "possibly in set" or "definitely not in set". Elements can be added to the set, but not removed (though this can be addressed with a "counting" filter). The more elements that are added to the set, the larger the probability of false positives.

#### Description
- A bloom filter consists of a big array of bits (with initial value 0) and a number of hash functions, says k hash functions.
- When an element is added to the set, its value is hashed k times and those k bits are turned on.
- When you want to check if an element is a member of the set, you hashed it k times and if one of those bits is 0, the element dose not belong to the set.
- Due to hash collision, false positive can happen, which means the process determines an element belongs to the set when it does not.

#### Benefits
- Much less space needed to store the occurrence of elements.
- Fast, since everything can take place in memory due to its size.

#### Sample Usages
- Check if a username is taken
- Cache filtering: only cache from second request
- DB query: only read from disk if bloom filter hits
- ...
