---
layout: post
title:  "Comments, LLMs, and identity on the internet"
date:   2025-10-11 12:06:00 -0400
categories: meta
---

# Why this blog doesn't have a comment section (yet)

(That's right, the first post on this blog is a meta post about the blog. That should set the tone going forward.)

While building this blog, I thought about the blogs that I enjoy reading, and one commonality among them is that I enjoy finishing a blog post and scrolling down towards the comments. Sometimes it's fluff, but oftentimes it's genuinely interesting discussion that enhances the _blog reading experience_. Personal anecdotes, corrections, critiques, or best of all: comments from the writer of the blog post. It's like getting more blog per blog! And while this might be a static site, projects like [utteranc.es](https://utteranc.es) still allow for comment discussion, at least on GitHub Pages sites, and while I don't love the lock-in to GitHub specifically, I could live with it.

And if this were 10 years ago, I probably would have added a comment feature without a second thought. I figure there's essentially no world in which this blog is popular enough that I become overwhelmed with moderation duties, and that's assuming anyone comments at all. Besides, most of my interactions on the internet have been generally positive, or at least constructive even when they're negative.

But LLMs[^1] exist.

# LLMs exist

I have a personal theory that **every interface on the internet, if it is open for anonymous unstructured submissions, will become completely unusable given sufficient popularity.** This is a direct result of LLMs existing and being widespread, and of the minute-but-ever-present financial and social incentives to spread content: advertisements, propaganda, flooding competitors' sites, plain old-fashioned trolling. Because LLMs have gotten good enough (and continue to improve) at producing content indistinguishable from humans at a rate much much higher than can be reasonably moderated by humans, those with money and a desire to spread influecne can and will flood every interface imaginable.

Perhaps one counterpoint would be "we can just use LLMs to do the moderation", but I don't think that math works out -- even assuming the LLMs have a 0% false positive rate for bot detection and a 1% false negative rate, the spammers can just increase their output by 100x and we're back where we started. And that assumes there really is abstractly anything different about an LLM-generated message and a human-generated one, especially for a short message. Remember, LLMs have memorized large portions of internet traffic, so the messages they output can just be regurgitated human speech.

You might also argue that the power consumption requirements of LLMs are prohibitive for what I'm describing. I think I agree that currently they are. This objection becomes less relevant over time, as global power generation increases, more datacenters are built specifically for LLMs, and LLM technology improves to use less power. (That last one is perhaps more of an assumption than the other two. While I don't think it's a given that LLMs get any better at impersonating humans, I think it is highly likely that the current LLMs are not the most efficient possible at the current level of output quality, and I think the current level of output quailty is enough to cause the above problems.)

# If you're right, shouldn't this already be happening?

It certainly _is_ happening on a small scale. Here's [Reply Guy](https://replyguy.com/), a service that will generate fake discussion about your product so that it shows up in Google results even if you're trusting Reddit to be a bastion of human discussion. We also all remember the 

# How much is it happening?

[According to The Independent](https://www.the-independent.com/tech/bots-internet-traffic-ai-chatgpt-b2733450.html) (citing a report from cybersecurity firm Imperva), 2024 marked the first year that the majority of the traffic on the internet was from bots instead of humans. This statistic made the rounds, and it sounds scary, but it's not really what I'm getting at. I don't care whether page hits are bot-generated, I care more about discussion.

How much of Reddit is LLM-generated? According to [this summary of Reddit's report on the matter](https://fraudblocker.com/articles/reddit-spam-bots), they removed about 3% of content for bot-related offenses. Of course, Reddit has something of an incentive to keep their numbers up and therefore allow lots of bot traffic as long as it seems legitimate, so we can safely say that at least 3% of submitted content is from bots. According to [this Medium article](https://captain-woof.medium.com/most-people-on-reddit-might-not-even-be-people-2b207a7f1902), about 10% of the posts in the subreddits tracked by the author (they didn't mention which subreddits) were LLM-generated, at least according to an automated scanner they used. Note that even assuming perfect accuracy from the scanner, this 10% would still include real people who turn to an LLM to write their post for them. However, we still run into the earlier problem that a bot can just replay earlier comments and conversations (whether that's being regurgitated by an LLM or just plainly copy+pasted on a repost).

[This Nature article](https://www.nature.com/articles/s41598-025-96372-1) claims about 20% of "chatter on social media about global events" comes from bots, with that number jumping up to 43.9% on discussions about the 2020 US Elections. That number is enough to raise red flags for me.

My broader point is this: I want to be able to go to a space, have a discussion, and know that I'm having that discussion with real people.

# Why does it matter whether you're talking to bots?

I'll fully admit that there are some spaces where it doesn't matter whether people are human. For example, I'm an occasional poster on [r/rpgdesign](https://reddit.com/r/rpgdesign). When I post looking for feedback or discussion on an idea, I don't really care whether the posts are coming from bots or not[^2], I just want ideas I can use for my project. On the other hand, if someone _else_ posts about their system looking for feedback, well, there might be something I can glean and use for my system, but if I'm going to reply and give advice I'd prefer that their post be genuine lest I waste my time responding to a bot. Furthermore, I would also like it if the other discussion that I fall into after my response is with humans, since I might be spending some time convincing them of things.

More broadly, another criticism you could have of the angle I take above is "well humans use LLMs to generate speech for them -- so even if it were all humans posting, wouldn't you still get lots of LLM output on any given forum? Humans also lie and cheat and steal, what good is gained fighting off the evil LLMs just to replace them with evil humans instead?"

There is a property humans have that I want to preserve: **persistence**. If a human says a bad thing to me in person, I can stop engaging with them, and then the next time I see them, I can recognize them and not have conversation with them. That persistence adds weight to their actions, allows me to make quick judgements and save time.

If a human uses their account to post a bunch of LLM slop, that's not good, but I can then ban them, and they can take accountability for that. I don't really care who wrote the post, it was your account.

This has already started to meander, so I'll summarize in a few bullets:
* LLMs can and will (and perhaps already do!) obliterate any interface you expose that allows them to submit content
* Therefore, if you want to open an interface to the wider internet without it being obliterated by LLMs, you have to have some rule that discriminates between people and LLMs
* You cannot do this on the basis of content alone because LLMs have gotten too good at producing human-like content; in other words, **LLMs pass the Turing test.** Therefore, the discriminatory rule must not be based on the content of what is being submitted, but instead some sort of metadata that establishes one's humanity.

# Should we just use government-issued IDs for this?

A couple years ago, when LLMs were picking up steam, I made a prediction that Meta would begin requiring drivers licenses or other government IDs to submit content because investors would start getting wise to the sheer number of LLM-fueled bots on their platform. My original prediction was that this would happen some time in 2024. While I was wrong on the platform and the exact timescale, recently YouTube [began requiring ID verification if they suspected you were a child](https://mashable.com/article/youtube-age-verifying-ai-how), nominally to keep children safe on their platform. While I generally dislike the amount of data these large tech platforms have, and their aggressive surveillance capitalism strategies, I actually think this is a genuine solution to a genuine problem. Apparently the answer to "what can a human do that an LLM can't" is "live birth recognized by the government".

At least, for now.

# What now?

I think this problem is going to get worse over time until it hits some critical mass. Maybe some big social media platform puts out numbers that staggering portions of their userbase are bots, their stock crashes, other platforms have similar investigations aimed at them, and there's an entire reckoning. Or maybe infrastructure like ID-based verification is slowly rolled out so as not to upset the apple cart at any moment. Maybe the bot flood stays at roughly current levels, and I just have to retreat to corners of the internet where the necessary infrastructure does exist. I don't know. But what I do know is that right now, opening up a comment section on a public piece of the internet seems destined to fail.

Email me if you want. Just prove you're a human first.

[^1]: I'm going to use "LLM" to refer to recent advancements in "AI". I don't like using the phrase "AI" to refer to what we currently have because I don't think what we have is really "intelligent" enough to clear that bar.
[^2]: Important caveat here: LLMs are an environmental scourge. The point here is that there's nothing inherently wrong with the discussion coming from bots. 
