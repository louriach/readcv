---
title: Are we too pedantic with semantic
description: By Luis
---
Before June 2023, it's safe to assume that most designers hadn't even considered the word "semantic" within their work.

It has arrived as part of the design tokens / Figma variables wave, and whooshed us all into a linguistic frenzy. What even is semantic, and why does it matter to **me**?

Well, it probably doesn't matter that much to all of us, because it is a design systems topic, and we're not all working on them! We can add *primitive* and *alias* into this bucket as well; terms on terms on terms.

**The terms**

I suppose we should probably define these terms before contesting them:

*Primitive*

When talking about a design token, it essentially means the raw value. The one for the value itself. For example, if you're familiar with Google's Material design principles, they have a large set of primitive values for colour:

* Purple 50 (#F3E5F5)

* Purple 100 (#E1BEE7)

* Purple 200 (#CE93D8)

* ...more colours...

* Purple 900 (#4A148C)

These numbers represent the darkness of a colour, 50 being the lightest and 900 being the darkest.

*Semantic*

This is where we introduce intention into our colour names. This means that:

* Instead of *Purple – 50*, they use "Surface Dim"

* Instead of *Purple – 500*, they use "Primary"

* Instead of *Purple – 700*, they use "On Primary Container"

As a designer using the colour, you don't need to know or care what primary actually looks like, it's just the primary colour you will use.

Hence, semantic because it's logical and has intention.

*Alias*

This is the process of referencing one value into another. Taking our purple / primary combination we would look at it like this:

*Purple 500 -> Primary*

The value of primary is purple 500, and it has been *aliased*.

**Alright Luis, what's the point of this article**

Over the past 9 or so months, I've become obsessed with semantics. Lots of people have.

"That's not semantic, try refactoring the name"\
"Primitives shouldn't be exposed to your design team, only the semantic values"\
"Primary means nothing, don't use that"

These are probably quotes I've said at some point.

I'm starting to reconsider whether we even need this semantic layer within token/variable architecture.

**-- From this point forward, I will be specifically talking about variables within Figma --**

It's a pretty bold turnaround, but hear me out for a second.

Variables within Figma have a feature called scoping. This allows you to say, for example, "this colour should only be used within a fill".

Whilst talking to a few friends on WhatsApp (hello [Luke](https://read.cv/finch), [Henry](https://read.cv/henrydaggett), [Hugo](https://read.cv/_hraymond), [Ollie](https://read.cv/strangutan), Scott, [Karl](https://read.cv/kejk), and [Gavin](https://read.cv/gavinmcfarland)) This sparked something for me recently, where I wondered whether scoping alone was the semantic modification we've wanted all along.

![Screenshot of the original WhatsApp message from Luis](/content/writing/pedantic-semantic-1.jpg)

Ultimately, semantic variables are a level of scoping, allowing us to define specific implementation of the values we want to control within a system. And if there's one thing I know, it's that agreeing on naming conventions within a design team alone is a near impossible task, and then tossing it over the fence to your engineers is another battle that may be lost as soon as you pass over the figma.com link.

Why? Developers love frameworks. I was ~~un~~fortunate enough to have been raised in the world of web development back when Bootstrap was the de facto standard. It didn't last forever, but we have other frameworks now plugging that gap, for example Tailwind CSS or Radix.

Tailwind CSS is fantastic for rapid development, because a lot of the design decisions have already been made. This is most certainly the moment where you start sweating, because I said design...decisions. For example, Tailwind CSS has a robust and well constructed set of colours, ready and warm from the oven.

These colours are primitive in nature, not semantic. In fact, here's a line from their documentation:

`Tailwind uses literal color names `*`(like red, green, etc.)`*`and a numeric scale`*`(where 50 is light and 900 is dark)`*`by default. We think this is the best choice for most projects, and have found it easier to maintain than using abstract names like`**`primary`**`or`**`danger`**`.`

Notice the callout to not use semantic naming here. Hey, this might not be that big a deal, but is almost certainly rage inducing for those that swear by the good book of semantic naming conventions. You *can* alias within something like Tailwind CSS into a more intentional semantic naming conventions, but good luck explaining why those hours of development time need to happen.

For Radix, I'd recommend reading their entire documentation [page](https://www.radix-ui.com/colors/docs/overview/aliasing) on aliasing, as they run into similar issues with naming.

What I think may be worth us thinking about is how we can become better friends with our developers, and work on their turf, rather than trying to crowbar in something that may not benefit the relationship.

**Back to Figma variables**

What's stopping us from maintaining a single, primitive set of variables, named as such (e.g. red-300) to match your developer's framework, relying on scoping alone to bridge this gap?

This also maps back to our Material design example too. Best served with a visual.

![Screenshot of the Figma variables window for the Google Material colours](/content/writing/pedantic-semantic-2.jpg)

The visual above shows our Material design colours for purple and teal, from 50 up to their darkest 900. 500 is highlighted, and has been scoped to just be available within frames and shapes.

This is exactly the same process we would go through for **semantic** variables, but we are only maintaining one collection here. This seems...logical? And perhaps less of a headache.

What would it look like with a real component example. Enter my favourite one, the toast.

![Toast component showing a comparison between the variables used. Left side is semantic, right side is scoped primitives.](/content/writing/pedantic-semantic-3.png)

There is a drawback here that you can't scope deeper. For example, "this colour should only be available in these specific components". But what's stopping that from becoming an eventuality if it saves us time?

Another potential issue is "what about dark mode?" This for me isn't necessarily a null point, but something definitely worth contesting. If modes should eventually "come for free" within our designs, does it matter if purple-50 is very light in light mode, and dark in dark mode? I'm not sure if it does. Within Figma, this would mean creating two modes at this primitive level instead. Visual below.

![Screenshot of the Figma variables window for the light / dark mode example.](/content/writing/pedantic-semantic-4.jpg)

Let me know what you think,\
Luis.