---
title: Loose thoughts: Variables considerations for multi-faceted systems
description: By Luis
---
Grab a drink, we have many words to read.

If you're working in a team with either multiple brands, multiple platforms, multiple densities, or perhaps all of the above you may be stuck trying to figure out how to structure your system/s in Figma. Here are some loose thoughts on how I'd go about approaching the problem.

### **Starting with small wins**

Organising and creating tokens in a design system is a 2-month or 2-year project, and you can start anywhere from documentation to auditing to creation. A useful starting point is to try and work from a position of low hanging fruit – are there any quick wins?

For example, are there any colours in your system that are already close to how you’d expect the end token to look?

I’m talking specifically about the Figma side here, where perhaps you’re looking at a transformation project to convert Styles into Variables. What I’ve seen is that this project seems simple, but opens large cans of worms with regards to naming conventions alone.

Perhaps you already have a `background-page` style, which will auto convert into a variable of the same name? Or you have a very consistent 4px radius on your main components – this is a moment where you could plan, create, add, and publish the radius Variable with little disruption to existing workflows.

Log these wins and aim to tackle them first.

### **Pipelines**

A key consideration to make throughout your token project is to define what level of automation you need. Honestly, I don’t think most teams need an automated pipeline of in/out changes from the design tool to the code repository.

Why? I doubt tokens are changing all that often! The energy to create a workflow may be better spent on other parts of your project to begin with, and trying to build better communication channels across your cross-functional partners.

### **Global or local libraries**

I believe that Variables are the “trojan horse” for a flexible system (shout out to [Giuseppe Perri](https://www.linkedin.com/in/giuseppeperri) for using the trojan horse phrase during a recent call), where we can be sure from a brand and systems point of view that the values are fixed, but introduce flexibility in their expression via team-level or local component explorations.

Knowing that all the colors, radius, sizes etc are consistent allows us to move away from the idea that the system is limiting creativity. It flips the idea so that we position components as something designers control, and tokens are something the system controls.

I believe this would promote higher adoption of consistent values and decrease the likelihood of value deviation.

At this point, we have the opportunity to consider what is indeed a global Variable, and what is more locally scoped to a platform, project, or feature. This is a significant ask, and may take time, but effectively the question is: what Variables and components does every platform use out of the box?

On a semantic level, within a multi-platform (mobile, web, car, watch, tv) system, you are likely to find that the values within each semantic Variable need to differ. For example, the screen quality of your car dashboard and mobile phone screen are likely to differ widely, so your `bg-danger` on mobile may alias `red-600`, but in the car you may need a higher contrast `red-700`. This technically can be handled by modes, but I’d like to question whether they should even be using the same primitive foundation at all?

For situations where your different brands or platforms do indeed need to use different primitive values, it might be worth considering using groups as a way to prefix Variables within Figma collections. For example, a group for Car, a group for Web, and a group for iOS. When aliasing these later on, you will be able to filter down to `Car/red-500`, which has a different contrast to `iOS/red-500`.

> For those interested, Figma has a different light and dark primitive ramp! You can see this in the published [UI2 community file](https://www.figma.com/community/file/1271813911103366792), on the page titled Color.

The challenge central to a goal of “one semantic for all” I think lies in sizing, specifically font sizes, density, and target sizes. Comparing a watch interface with a tv one will immediately make life challenging. A `heading-hero` font size will vary massively across platforms, so we need to decide if we want to maintain separate style libraries for these different platforms, or rely on a mode-based approach to handle all of the individual values.

A curve ball option on this too is to use components for your text styles, which might actually align tighter with your code implementation anyway!

The pro of centralising all of your values (using modes for platform switching) is that you are tightening the screws of control within the system. This is great! For you, the system maintainer 😉. You minimise risk of duplication, and align closer to code implementation.

On the con side of the equation, you expose all designers to all modes. A designer working on mobile still has access to the car, tv, and watch Variable modes. To me, that’s quite a high risk of walking into a mixed mode world, where we push a piece of work to production using the wrong colour values.

Perhaps I’m being dramatic, but it’s potentially expensive. Additionally, depending on how clear you are with your mode names, a darker shade of red might “just look better in a different mode” for a designer, again risking mixed modes.

In a highly functioning or tightly knit team, this risk is small because communication and documentation can discourage the mixed mode approach, but it’s still a risk.

**Splitting libraries**

With these considerations, we might then want to explore splitting our platforms into separate Variable libraries. One central library is great in theory, but the volume of Variables you’d have to maintain in a single collection across many themes, brands, and platforms could soon explode.

Inefficiency is the canary in the coal mine of an ambitious systems team, but I believe that sometime debt or less efficient approaches to management can help unlock way larger efficiency in our dependent design teams.

Similar to the concept of snowflake components, we may be enabled to manage platform-specific Variables if we opt for a split library approach. Say our watch interface has a specific `pill` component for `alerts`, this doesn’t need to be global and in fact may cause disruption if it is.

Additionally, because it’s a platform-specific component with its own behaviour, we have the opportunity to debate whether component-specific Variables would help us release and manage this too. Component Variables are given a bad rap, a lot [by me](https://youtu.be/M0NU5QFLCl4?si=ip-ijUmNuZWGXADL&t=607), but they have their place. Perhaps more on this in another article.

### **Design and code deviations**

Within Figma right now, there’s no ability to:

1. Add percentage Variables (for things like line height)

2. Add opacity as an override to a Variable

Because of this, we have to accept that Variables in design, and tokens in code, will differ. We have a few workarounds, but fundamentally we have a deviation.

On the line height side, I currently do not use Variables for line height in my text styles. I add a % value manually, unless working with a strict pixel based system of course!

For opacity, I do one of two things:

1. Create an additional primitive. For example, our `red-500` example may need a version that’s 70% opacity. For this, I would create a new Variable called `red-500-70` and then alias this into my semantic Variable. The benefit of this is that we can remap or reconfigure the semantic Variable later, because we know where the primitive is applied

2. Alias in my `red-500` Variable to the semantic one, and then detach the Variable. I then set the 70% opacity on the raw hex value. This idea may raise your eyebrows, but it’s a quick and dirty way to prevent the need for additional primitives. This is the approach I have taken in the [shadcn UI kit](https://www.figma.com/community/file/1414738876845632189) I've been working on

Both of these options are likely not how we would be managing things in code, so do bear that in mind at the point of build. Communication between teams may be a quick way to resolve this.

### **A quick moment of existential thought**

It is an existential question, but at these points of deviation it does beg the question – do design and code *need* to be 1:1 aligned? Is Figma the exact replication of what you have in code, or is Figma the playground for ideas, perhaps in a different way?

Parity here means we might need to bend over backwards to ensure naming conventions and values are very tightly matched, whereas answering no might mean "hey we don’t even have half of the Variables in Figma", and they have different names altogether because designers think in a different way.

All of this will also be defined by who we decide is responsible for maintaining and updating Variables and / or tokens. If it’s all the design side, you may have flexibility. If all on the developer side, you may need to align a lot closer. Or not!

Again, a conversation may help resolve a lot of these potential concerns.

### **A Mille-Feuille of Variables**

Classically, we look at the 3 layers of Variables being primitive, semantic, and component, but in order to build truly multi-dimensional setups within Figma we might have to introduce many more.

With Figma’s Extended Collections feature being delayed, we have to explore different ways of managing multiple dimensions within our Variable setups.

> [Kish](https://x.com/IAmByDesign1) explores an option over on [YouTube](https://www.youtube.com/watch?v=zCCEn6zFlDY) if you want to see how he is thinking about things.

To me the simplest way to introduce complexity to enable complexity is to consider a middle layer of “brand” within our setup. Perhaps we go from primitive into brand, where we introduce light / dark, and *then* into semantic. That middle layer is where we can use modes for different brand (or perhaps platform!) specific definitions of our Variables.

This is definitely tricky, as we could end up maintaining duplications of the same Variables across different collections, but enables us to manage primitives, colour modes, and semantic naming conventions within a single system without exhausting the modes available to us.

```
I'm fully aware that this is probably best served with a demo, so I might add one in later.
```

Once again, this is not how we would handle things in code, so bear that in mind! It is worth considering if this is actually a problem if at the point of inspection your values present on components are correct and your developers can see them.

### **Mega components?**

A central system dream state will be where you pull in a component from the library, and you’re able to switch it to a different platform, mode, or density quickly and with great performance.

Whilst this is technically possible, there are a few ways to get there:

1. A variant component containing all brand, platform, and density expressions. AKA the *mega component*

2. Using Variables and modes build multi-dimensional setups like we mentioned before

Option 1 is definitely the pre-2023 logical approach, but do bear in mind that in Figma, every single component variant is loaded onto the canvas when you insert them. This means that a large variant set potentially has the ability to slow your file down with a large amount of inserts.

Option 2, whilst desirable, lands us in the situation mentioned before with the need to create multiple levels of aliasing to achieve the desired approach.

A third option is to maintain many, seemingly identical component libraries. This impacts every decision from text styles to component composition to library permissions to naming conventions to code parity.

That’s a lot to consider! But, I would like to propose it at least as something to think about. Why? Versioning!

When working on multiple different codebases and platforms, with different release cycles, you may end up in a sticky situation where a single component for everyone doesn’t allow you to release the next version for a specific platform.

Does your card on v4 of the web app need a button at the bottom, but you don’t need it on iOS? Sure, you could introduce a boolean toggle in the main component, but nothing will prevent a designer toggling it on accidentally for the web. To me, this suggests an iOS-specific card component, even though the radius, colours, spacing, and states may be identical.

Mmm, but what about discoverability? Two seemingly identical component libraries might cause a headache when trying to find the right component. Technically yes, this is true. We can move around it with library permissions (switching on the iOS library for iOS designs), but for those that work across multiple platforms within the same file, we will still have the issue.

This is perhaps where name spacing can help. Does `card – web`, `card – iOS` allow you to manage these independently, whilst aiding discovery? It does vary on how your designers find components as well – do they use sticker sheets, copying and pasting between files? Or do they search in the assets panel for specific components? Either option may help or hinder this idea.

It’s worth mentioning – and I promise I’m not trying to sell here – that [Code Connect](https://www.figma.com/blog/introducing-code-connect/) within Dev Mode may make this redundant too. If you are connecting the correct coded component to a Figma one, naming conventions may not need to be aligned at all. `Card` may be called `Tile` in code, and that might be an issue if, when inspecting, your developers can see the correct code regardless of name.

### **Naming convention comprehension**

Something to bear in mind from a systems perspective is whether people even understand what your agreed names even mean. Of course, “naming is hard” etc, but understanding differs within seniority and interest levels.

1. Does a junior designer understand what `bg-default` means?

2. Does a senior designer know that `bg-danger-tertiary` should only be used in combination with `fg-danger-tertiarty`?

We must anticipate these differing levels of knowledge when it comes to naming conventions, and try to build systems to support. Sure, the easy out here is to write documentation on how and when to use specific Variables, but I’d challenge it.

Do we then need to be in a position where we’re managing multiple levels of naming, to aid the rapid iteration of design ideas? Is it actually *that bad* if someone prefers searching for `orange` instead of `bg-notice`?

### **Surprise! We have a design system**

Lastly, I think, is that as with any significant project rollout, we must be mindful of anticipated reception.

Does your design team know you are working on a large Variables project, and that what they are currently doing is due to change? If they do not know, then tell them immediately! And do it so often they get bored.

The worst thing for a project is to have the recipients feel like the rug has been pulled from underneath their feet, and especially when an organisation is moving at pace.

\--

Questions? You know where to find me 👋