---
layout: post
title:  "Game systems, content, and closed vs. open universes"
date:   2025-11-01 17:46:00 -0400
categories: ttrpg
---

# Content-agnostic game systems

Tabletop roleplaying games (henceforth TTRPGs) and trading card games (hereafter TCGs) have an interesting thing in common -- they're both abstract systems that are largely meant to be "content agonstic". Using 2014 5e as our stand-in for a generic TTRPG, a _shortsword_ is a martial melee weapon, costing 10gp, weighing 2lbs, with the **Finesse** and **Light** properties, dealing 1d6 Piercing damage on hit. All of that information is "stored" "in" the description of the shortsword. You could remove the shortsword from the game, and apart from a few class descriptions that either start with it or start with proficiency in it, almost nothing would break. You could also add another 50 similar weapons to the game, and nothing else would change.

Contrast this with an RPG video game like _Dark Souls_. There are a fixed list of miracles, pyromancies, and rare weapons in that game. In fact, for each of those categories, there is a Steam achievement for collecting all of them. Consider trying to implement such an achievement in 5e -- what do you mean, "every rare weapon"? As if a new module won't come out next month, introducing another 10 new weapons, a couple new spells, maybe even a new subclass. The assumption is that the world is infinite, that there are always new creatures to find and slay, and you only observe some small portion of that world.

For a more concrete example in the form of a TCG, we can turn to Magic. Consider the rules text for Diligent Zookeeper, a card that was (at the time of writing) recently spoiled for the _Avatar: Last Airbender_ set:

> Each non-Human creature you control gets +1/+1 for each of its creature types, to a maximum of 10.

Note that "to a maximum of 10" part of the line. Compare this with the rules + reminder text of Changeling:

> Changeling (This card is every creature type.)

If not for that maximum of 10, how many bonuses would a Changeling get if we removed its Human creature type but left all other types? We would have to consult the comprehensive rules for a list of all creature types, find that the list is 309 types long, with 4 more having been teased. This list changes constantly as new types are introduced and old types are retired and absorbed into existing ones.

Now, this doesn't really matter for Magic, since while this would be an arcane interaction, it's at least well-specified, and that's all that really matters. But when designing a TTRPG, we often care about maintaining some semblance of internal consistency, some sense of sense-making, to our effects. If you tried moving the above interaction into a TTRPG it would be nonsense: the affected creature would become more powerful as...new creature types were discovered? Codified into the rules? Does a giant global list of creature types exist somewhere in your world? When are new types added to the list? Who maintains it? Could the adventuring party find it and add to it to make their member stronger?

# "Closed" and "open" universes

Let's say we're developing a new fantasy TTRPG, in which we have a cool weapon called a _Fire Sword_, and a cool enemy called an _Ice Giant_. While running a playtest, a player swings their Fire Sword at the Ice Giant. It hits! We, the GM, inform them that it does 3 damage, the same as it does to any other enemy. The player becomes some mix of confused, crestfallen, and cantankerous. "That doesn't make sense!" they proclaim. "The Ice Giant should take extra damage from the Fire Sword! Fire melts ice!"

Let's assume we wish to acquiesce to their claim, and specifically we wish to do so in some systematic way: we want to codify the fact that the Fire Sword does more damage to the Ice Giant, while also avoiding such negative moments in the future. How might we do this?

I can think of several ways of writing this into a system. In the following, the part before the colon will represent the section of the system that contains the rule after the colon.

We could specify this exact ruling on the Fire Sword itself (we'll call this option A):

> Fire Sword: This weapon deals extra damage to Ice Giants.

We could also specify the exact ruling on the Ice Giant (option B):

> Ice Giant: This enemy takes extra damage from Fire Swords.

We might want to be a bit more general (option C):

> Fire Sword: This weapon deals extra damage to Ice type enemies.
>
> Frost Giant: This enemy is Ice type.

...or again, the reflected version (option D):

> Fire Sword: This weapon is Fire type.
>
> Frost Giant: This enemy takes extra damage from Fire type weapons.

And finally, we could combine both of the previous indirections (Option E):

> Fire Sword: This weapon is Fire type.
>
> Frost Giant: This enemy is Ice type.
>
> Main Rules: Fire type weapons deal extra damage to Ice type enemies.

Now, for the scenario that came up during playtesting, all of these options have the same immediate effect: the Fire Sword will deal extra damage to the Ice Giant. The difference between these rules comes out in how they generalize to other scenarios that come up in the future, and how we write content in the future.

## Option A

Let's examine option A first. It's perhaps the most straightforward solution, but it's also not a great idea. Why? Well, let's say later down the line, either while adding content to your base Creature Compendium or while writing a new module or homebrew or _whatever_, you decide you want to add a Frost Spider as a new creature. Cool! You write up the stat block, you go to playtest, and the exact same scenario as above plays out, except this time with the Fire Sword against the Frost Spider. Sigh. You have kicked the can down the road, but not really solved the problem. (In fact, you might have even incensed the player slightly more, because now there is an existing interaction/precedent for what they're trying to do, but this new enemy doesn't follow that precedent.) So now you have two options: you can either go back and errata the Fire Sword to say

> Fire Sword: This weapon deals extra damage to Frost Giants and Frost Spiders.

...or, even worse, you can update your Frost Spider to say

> Frost Spider: this enemy takes damage in the same way as the Frost Giant.

Gross. And as you continue to print Frost Wolves and Frost Spirits and Frost Elves and Frost Imps this problem will raise its head over and over and over again.

How did we cause this problem? My initial thought, and perhaps yours, is that _we made the Fire Sword responsible for how it interacts with every enemy_. I don't actually think this is the problem, so we'll come back to it.

## Option B

The crafty TTRPG designer you are, you update to Option B. Now, when writing the Frost Spider, you include a line of text that says

> Frost Spider: This enemy takes extra damage from Fire Swords.

Great! Problem solved! And in fact, you can now print a wide variety of Frost-related creatures that all take extra Fire Sword damage.

Anyways, later, you're playtesting, and you give your player a Fire Halberd. And the exact same scenario plays out, except with the Fire Halberd against every single Frost-related enemy you've introduced.

We can see that this is the "mirror" option to Option A, and it has the "mirror" problem: with Option A you could freely introduce more Fire weapons, but not more Frost enemies; now you can freely introduce Frost enemies, but not new Fire weapons.

Now I think the issue crystalizes a little more: the problem is that while yes, there are only so many weapons in the system _right now_, we don't much care to lock ourselves into that list. We want to write our rules in such a way that the list of weapons could continue to grow in the future, and we won't have to go back and update all of our previous content to match. In other words, we would like to have an _open universe_ of weapons, as far as the system is concerned. However, we would also like the set of enemies to be an open system, as we continue to introduce new ones in future modules. And finally, we want to have rules that call out specific interactions between subsets of those weapons and those enemies, but in a way that doesn't involve explicitly writing out lists of either weapons or enemies, beacuse any such list is inherently going to be out of date.

How do we do such a thing?

## Options C and D

We introduce an intermediate, _closed_ universe! That universe being damage types. With Option D, we can print as many Fire-type weapons as we like, and then when we go to print our Frost Badger we can give it that magical line of text:

> Frost Badger: This enemy takes extra damage from Fire weapons.

And we're on our way. This is exactly what 5e does with damage types and vulnerabilities. Our problem is solved!

There's a cost, of course. We have to have a closed universe _somewhere_ to make this work, and we decided to put that onus on the list of damage types, so we better be sure we have a complete list of damage types forevermore. While the list of weapons and list of enemies is all external and modular, the list of damage types becomes **part of the system**. If you later want to introduce a new weapon that deals a new type of damage, that's not a content change, that's a system change.

This is where the difference between Option C and Option D rears its head: which one you choose depends on whether you think it's more reasonable to have a closed list of damage types as in Option D, or a closed list of "enemy types" (Frost in our running example) as in Option C. 5e thinks it's easier to do damage types, and they're probably right -- there are many ways for a thing to be, but only so many ways to destroy such a thing.

## Option E

You would think this would somehow be the "best" option, but I don't think it gets us much. We only needed a single layer of indirection to solve our universe problem above, so adding another one doesn't mean much.

# Use-case: what's wrong with Diligent Zookeper + Changeling?

Taking the knowledge we have, we can better understand why the Zookeeper Changeling example goes wrong:

We can quickly identify our problems:
* Creature types certainly want to be an open universe.
* Changeling, as written seems to want creature types to be a closed universe. However, almost every other Magic effect that cares about creature types only really cares about membership in a fixed group (e.g. "Cats you control get +1/+1"), and if we institute a design rule that this is the only way we will interface with creature types, Changeling is actually fine with an open universe of creature types. To see this, we could rewrite it as "this creature passes all checks for membership in a specified creature type" and most Changeling-related interactions would probably still work.
* Finally, Diligent Zookeper certainly wants a closed universe of creature types, since it cares about the number of them.

# Use-case: crafting systems

I've been thinking about this because I want to make crafting work in a TTRPG. Consider the universes we must maintain: creatures, items/recipes, and materials. I'm not sure I want _any_ of these to be closed universes:
* Does it make sense to write down the sum total of what a given creature can drop? I might write down that a magical boar drops its tusks, but if I then want to make a recipe for a cold-resisting armor set that requires magical fur, could they not take it from the magical boar? This would be solved with a closed universe of materials.
* Does it make sense to write the list of recipes on the material? Probably not, because recipes are usually an AND from the player perspective ("you must have at least all of these ingredients") so specifying partial information ("this feather could contribute towards the creation of some winged boots") isn't very helpful. (Unless you decide that each recipe needs only e.g. 3 materials that are listed as contributing towards it, but I dislike that system for many reasons.)
* Should recipes refer directly to the creatures they require? We could say that a Fire Sword requires a Fire Material of at least Grade B, or we could say it requires the flame sac from a Dragon. But now we've closed off the universe of creatures. This is my latest line of thought: perhaps we could parameterize over the _properties_ of the creature, thus closing not the universe of creatures but the universe of mechanics that creatures are allowed to have? The flame sac from a "dragon", where a "dragon" is any enemy that is at least Large, can deal Fire damage, and can fly. Are all such things Dragons? Perhaps by some definition of the word. But then, a human who learns to cast the right spells could satisfy each of those requirements. They would "functionally" be a Dragon. If you killed them in such a state, could you harvest a flame sac? There's a sense, perhaps, in which you ought to be able to harvest _whatever_ lets them do such things...

If I had a comment section, this is where I would invite discourse.

# Footnote: Magic isn't _really_ like this, by the way

While yes, Magic needs to be built in such a way that they can continually print new cards into the existing system, Wizards is much more prone to updating the rules of Magic to enable some new mechanic or card. In fact, certain cards even get bespoke rules just for them, which is pretty much the antithesis of this whole design pattern. By comparison, TTRPGs have to deal with this because there's a widespread expectation that GMs might create their own content for use in the system, often on the fly.
