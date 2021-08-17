## Twitter Giveaway Bot

Date: 02/27/21

Way back when in late 2019, I became aware of this absolute genius of a man through a DefCon YouTube video [here](https://www.youtube.com/watch?v=iAOOdYsK7MM) who essentially used Twitter's API to enter every single Twitter giveaway on the platform, and he ended up winning some pretty cool stuff. I was super impressed and wanted to build something like that out for myself, as I'm a real stickler for free stuff :)

So that year I built out a [program](https://github.com/WilliamHYZhang/Twitter-Giveaway-Bot), registered for a Twitter dev account "for educational purposes" and all that jazz, and I think in two weeks or so got banned, LOL.

Anyways, I came back to it over the past winter break and was determined to make it better. I think it took a couple hours to just revamp that old code and make sure I wasn't at risk of getting banned again. Previously I had it running on my regular computer, but now I have an old Dell desktop that I configured to be run as a Linux server so the code is just running there now.

Some notes about what I had changed:
- No more follower churn/queue, mainly because it was too risky.
- Same thing with likes, I removed the liking feature entirely since I'm pretty sure that's why I got banned last time.
- Limited following.
- And finally, probably the most big brain move. To maintain a healthy following/follower ratio, I now farm follows by tweeting "giveaway-like" tweets every so often, and have bots that OTHER people create like, follow, and retweet :))

And yeah, that's pretty much it. I've mostly won some small stuff like Pokemon codes, Roblox stuff, and other video game prizes that I'm too lazy to claim but I check in with it every once it a while. Check out the bot in action [here](https://twitter.com/LuckyWillyV2).