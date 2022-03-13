---
layout: post
title:  'Twitter ENS Analysis'
date:   2022-03-13
permalink: 'posts/twitter-ens-analysis'
---

There's a lot of fishy stuff going on in the crypto/web3 space, which prompted me to wonder, "What percentage of .eth Twitter handles/names actually resolve to an address?"

This weekend, I found out. Here's how.

__TLDR: depending on the user category, anywhere ranging from 2-10% of domains DON'T resolve to an address.__

# Setup

The basics are pretty simple. We want to scrape Twitter profiles with '.eth' domains, and lookup if these domains resolve to an address.

To scrape Twitter profiles, I used the Twitter API (have a developer account from an old project that I still need to port over the blog post for) and the Tweepy wrapper.

I don't think there's an API for ENS lookups, so I just performed a rate-limited GET request to etherscan's ENS lookup tool with a believable user agent and parsed the return HTML.

Results were written to a file and then parsed/analyzed later. The scripts took around an hour to code, mainly due to fiddling around with rate limits and Twitter's search queries. The runtime of the scrape job was around 6 hours.

# Results

A total of 2853 users were sampled across different categories such as art and NFTs. Here's a breakdown of the basic statistics:

| Category     |  Total  |  Invalid  |  Percentage  |
|--------------|---------|-----------|--------------|
| Population   |  2853   |  141      |  4.94%       |
| General      |  872    |  18       |  2.06%       |
| Art          |  786    |  51       |  6.49%       |
| NFT          |  479    |  46       |  9.6%        |
| DAO          |  716    |  26       |  3.63%       |

Side note: bro why does this Jekyll theme produce such terrible tables? If anyone wants to help me fix the spacing lmk.

See the code and some more graphs (follower/following data) on Github [here](https://github.com/WilliamHYZhang/Twitter-ENS-Analysis).

# What Does This Mean?

I'm interested how invalid ENS domains relate to web2.0 link rot. It's cool that the population 4.94% of invalid .eth domains is quite close to the [6% of inaccessible links from 2018 sources](https://www.theverge.com/2021/5/21/22447690/link-rot-research-new-york-times-domain-hijacking) (around the same time as the start of ENS).

I think that we can treat this invalid .eth domain percentage as a measure of the maturity of a certain sector of the crypto world. A user having an invalid .eth domain either means they lack the intellect to configure their domain correctly, the domain expired, or (most likely) they are simply obliviously buying into the crypto hype. For example, I mean just _look_ at the NFT invalid link percentage (~10%). Yeah, I'm not getting involved in that shit anytime soon. On the other hand, I'm impressed at the "maturity" of DAOs, they seem to be pretty nice (I don't think I'll fall for a DAO scam).


# Limitations

- Twitter only surfaces the top 1000 accounts given a search query, which results in massively popular accounts being returned first. This is why the "General" category with only an '.eth' query had such a low percentage of invalid domains. Adding specific categories helped reduce this bias towards popular accounts. Nevertheless, I believe the true percentages across all categories are probably a couple points higher.

- The regex for domain search should also be matching against dashes.
  
- In hindsight I realize that these categories are likely to be non-disjoint, so the set I used to prevent duplicates across categories should probably be removed.

- Kicking myself for not exporting as a CSV in the scrape job instead of crapping out a text file.
  
- Apparently '$' is an invalid Twitter query, but I'm not running that 6 hour scrape job again.

If anyone wants to address these limitations or just make this analysis and data collection process more robust, feel free to open up a PR on my repo.

# Conclusion

Anyways, this was a pretty neat project. I was honestly expecting the percentage of invalid links to be significantly higher. I'm not a full ETH bullhead; although I 100% believe in the cryptography and technical research towards the blockchain, there are a bunch of dubious projects and grossly inaccurate buzzword usage (cough cough zkSNARKs) over the media that make me skeptical. It was a pleasant surprise that most domains were real!