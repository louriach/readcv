---
title: 💡 Loose thoughts: No variable is an island
description: By Luis
---
I have a hunch – “semantic variables” aren’t what we think they are.

Are you suitably provoked? Okay, let’s proceed.

The – or at least my – definition of *semantic* is that as a consumer of a design system, I can confidently and predictably pick a variable. That seems pretty straight forward, and something we should also feel confident building for, but I don’t think this is happening at scale.

### **Which brand?**

If we take the example `bg-brand`, a quite common name for a colour variable. Sure it tells me it’s a background and it has a brand color as the fill.

But I challenge this simplistic view:

1. In a multi-brand organisation, *which* brand is this?

2. In an organisation with multiple options for brand color, *which* one is it?

3. In a situation where you have different tints or emphases of a brand, *which* one is it?

![A visual exploration of Brand A and Brand B, showing their primary and secondary colours.](/content/writing/variable-islands-1.jpg)

For those working in brands where your primary brand colour is unfortunately orange or yellow, you are likely trying to run away from using them because of their challenges with accessibility contrasts. This may mean that you use a secondary (complimentary) brand color, acting as a pseudo primary colour when used in an ordinal system.

In this scenario is primary…secondary? No, it’s still primary, we just don’t use it. Thus forcing a thinking exercise where you convince yourself that secondary is primary.

To those of you working with brand colours that are indeed red, yellow, or any colour typically associated with a component’s sentiment, I wish you luck.

### **Latinate ordinal numbers**

Despite the above title looking like gibberish, that’s the technical term for *primary*, *secondary*, *tertiary* etc. These are also very common naming conventions in the land of variables.

Despite familiarity and commonality, I'm slowly but surely coming round to the idea that `background-secondary` is not a semantic variable. Semantic should mean clear intent, but an ordinal system like primary, secondary, and tertiary doesn't actually tell you *where* they should be used and for *what*.

![The Figma variables panel, showing a set of colour variables. There is a pink circle around a group for bg/default. There is a label on the left hand side circling two groups – default, neutral – with a label reading "fuzzy intent". There is a second arrow on the left hand side pointing to another set of groups – brand, positive, warning, danger, disabled, utilities – with a label reading "clear intent".](/content/writing/variable-islands-2.jpg)

> The above image was originally posted as a [tweet](https://x.com/disco_lu/status/1848711886839165003).

Don’t get me wrong, I spent *hours and hours* playing around with these methods of building color palettes and components whilst working on [Simple Design System](https://www.figma.com/community/file/1380235722331273046/simple-design-system) at Figma. What became tricky during this work was building  predictable combinations of colour, which I believe is central to the successful adoption of any system.

I kept banging my head against a wall when trying to compose components, patterns, and screens where I wasn't even sure myself which ordinal to apply in which position; and I made the system!

For those building a design system, a latinate ordinal system is assumed knowledge based on a widely accepted belief that it is *the right thing to do*. Fantastic systems like [Polaris](https://polaris.shopify.com/) popularised this naming convention, and that’s great! But for those *not* working in a systems team, are these conventions understood?

### **In practice**

Let’s say you’re building out a screen. The container background is white, and you’d like to add an informational section in a light grey – a common scenario.

![An example page layout. There is a light grey background, with a white container in the center. Within the container is a set of dummy text, set in a block font. In between two paragraphs, there is a light grey coloured block with more example text inside.](/content/writing/variable-islands-3.jpg)

As a designer, what is your instinct when applying a colour to this section? Based on familiarity within commonly referenced systems, you’d be forgiven for suggesting something like `background-secondary`.

Now, because I spend way too much time thinking about this, I have some questions:

1. Would we choose secondary because we want it to look less intense than the high contrast white?

2. Or secondary because it’s the second most prominent element on the page?

3. Or secondary because of the hierarchy within a section?

This all leaves me with more questions than answers, and suggests a black hole of documentation is ahead.

What baffles me even more here is that in terms of elevation, this secondary element is *above* the background, which would be safe to presume is in fact *primary* in this case. It’s secondary, but in reverse order. My head hurts.

### **Dark mode doesn’t help**

In dark mode, the colors become interesting too because as the elements raise in elevation, they typically get *lighter*. This means that the secondary in reverse problem pops its head into our lives yet again, with my semantic brain exploding at the thought of something named secondary being more prominent than we want.

![The same dark mode variant as before, but the inner callout section has been made darker than the background it sits on.](/content/writing/variable-islands-4.jpg)

You could recess the element, making it feel more secondary, yet it’s still standing out like a sore thumb. And…we’re digressing very far from the original point now.

### **Deepening the problem**

I’ve spent a lot of time here talking about the problems of the primary and secondary variable naming conventions, but tertiary also doesn’t help us.

![The light mode example section from before, but a "sidebar" style element has been added to the right. There is an arrow pointing to its background, with a label "tertiary".](/content/writing/variable-islands-5.jpg)

In this example, which I’ve arguably engineered to be confusing, we have a tertiary sidebar element which definitely has less prominence! It works! But secondary still exists as being more prominent against the white.

With tertiary here, it’s the **second** most prominent *main* element on a page, but is using a **tertiary** value. Someone please help.

Just to be clear here, these are deep and perhaps unnecessary questions, but that’s what I’m here for.

### **Components**

Wait, isn’t that little banner inside the main container actually a component and all of this is a useless academic investigation? Probably.

![The callout section is now wrapped in a bounding box, similar to the selection style of Figma elements. It has a label above reading "❖ Callout". There is an arrow pointing to its background with the label "Bg callout".](/content/writing/variable-islands-6.jpg)

This is essentially what I’m getting at – a semantic decision should be understood and predictable. There’s a challenge with naming where we must strike the balance between too narrow (specific) and too wide (non-specific).

In my opinion, a latinate ordinal number is not semantic because it’s too open for interpretation and therefore too wide. In a similar vein, using a different example, `shadow-video-thumbnail` is too narrow, and restricted down to too specific case, compared a more generic, useful, and scalable `shadow-card`. Cards are everywhere, thumbnails are perhaps on just a few pages and this smells like a red flag for consistency being deviated in a system.

What I feel here is that because we are introducing ambiguity with an ordinal system, we’re straying far from semantic conventions and back into the deep dark world of primitives.

### **Are ordinals actually primitives?**

Here’s a challenge: is `background-default` actually a…primitive? What does `background-default` even mean? Let's assume we're working with `#fff` here, should we apply that to every single white element? When you put it like that, the answer becomes a very clear "no".

![A light and dark mode representation of a simple box on box layout. The background has a label "background-page", the foreground "background-section".](/content/writing/variable-islands-7.jpg)

This is specifically the case when you look at a dark mode implementation. White on white may be totally fine in light mode, but we likely want to introduce tonality in dark mode, perhaps a lighter foreground. Our `background-default` falls on its face very quickly, because we need nuance across modes.

A more specific `background-page` would allow for a fixed white / dark grey across modes here, whilst a `background-section` would promote deviation for the light / dark switch.

### **No variable is an island**

In isolation, a variable has no impact. Any colour decision we make is only relevant in the context of *other* colours. A radius variable must be balanced against its child and parent, so that we can build visually balanced corner radii in our designs. Any line height value is variable when used with different fonts and casing.

Therefore, no variable is an island. They must work together.

It’s at this point where we start to challenge all previous knowns about naming conventions because we need to consider *pairs*. Does `color-text-secondary` only work on `color-background-secondary`? That’s unlikely, but when looking at colours with a hue, we may end up there.

![A pill component variant set in varaious different colour schemes, in both light and dark mode.](/content/writing/variable-islands-8.jpg)

When building [Simple Design System](https://www.figma.com/community/file/1380235722331273046/simple-design-system), I toyed for *hours* trying to build a complimentary component set for badges and messages. We scrapped this idea in the end for the sake of simplicity, but the token system does still exist, presented below.

![FIgma variables, showing groups for text and background colours and their combinations / pairs.](/content/writing/variable-islands-9.jpg)

The challenge is that you, as a consumer of these variables, have no idea that they are recommended pairs. There is nothing stopping you from applying `text-warning-tertiary` onto `background-default` and failing accessibility ratio targets of 4:5.1 even though it is a very close 3.97.

### **Linting**

Where I believe this lands us is a world relying on linting to catch system deviations. Linting has become *the* way to ensure that designs are accurate, accessible, and consistent, but is this happening more often than we need to based on the arguments above?

An unpredictable search experience for consuming variables introduces a point of failure in usage. This trickles down to teams requiring more linting to catch usage errors. The lower our (the designer) confidence in the choices we are making, the higher the requirement for someone else to lint our work.

I can see this leading to a dissatisfied team.

### **Semantic, but at the component level**

I believe that our semantic dreams are still achievable within this ordinal context, but only at the *component level*.

A primary button is very clearly defined! So is a secondary one! This makes me happy. The values within it though are where we return to the predictable, searchable, and self-documentating variable values from before – `color-background-action`, not `color-background-primary`.

Just to re-clarify, primary here is ambiguous in that it insinuates the most used element, but in reality is the most prominent. A primary button however, is way clearer in how it should be used.

### **The problem with default**

If you’re building any software in the year 2024, there’s a high likelihood that you have a set of very common patterns – *cards*, *panels*, *popovers*, and *toolbars*. These often share the same properties, perhaps a background color.

Similar to a previous example, when we introduce branding or system-level dark and light mode switches, we may want to deviate from this notion that they are all using the same values.

This is where we often come across…the **default problem**.

![An example white page, with a white section on top, and a white popover on top of that.](/content/writing/variable-islands-10.jpg)

Again, we’d be forgiven here for following common accepted knowledge that your most used element in a system is called the default option. I prefer the word *base*, but that’s a different conversation. Anyway, we hit another dark mode wall when we want to use elevation to indicate elevation.

![The same section and popover combinations from before, but set in dark mode. Here, the colours are not all the same, with them getting lighter as they elevate.](/content/writing/variable-islands-11.jpg)

As your elements gets *closer* to the eyes, you are likely to want to use a lighter color in dark mode. This means that default needs to be split, and we lose our control. Designers at this point have probably detached your variable and gone freestyle.

This is why it’s logical to split these variables up into their dedicated end points or use cases. `background-default` doesn’t scale across modes, so introducing `background-page`, `background-popover`, and `background-section` enabled variance within the system, whilst still protecting your goals of cohesion and contrast.

![A visual showing light and dark mode variations of the previous screens, but the variables applied are specific – background-page, background-section, and background-popover.](/content/writing/variable-islands-12.jpg)

`background-card` is more discoverable when you’re making…cards, `background-panel` for when making…panels, `background-popover` for…you get the idea.

These are likely to share the same values, in fact they almost certainly will, but I don’t think this is a problem. The marginal memory increase in your token file is far outweighed by the efficiency and predictability gains on the consumer side. Hey, it may also reduce the need for so much linting.

It may sound like I’m ringing an alarm bell for component-level variables here, and you know what? Maybe I am on the surface, but this aligns with my proposal for *Functional* and *Presentational* tokens from the T+CPS framework pitched over in my other article about [atomic design](https://read.cv/disco_lu/rethinking-atomic-design).

A `panel` is a *presentational token*, a `tab` is a *functional one*.

### **Token pairs**

Finally, and very quickly, I'd encourage you to watch this snippet from the Asana talk at Figma's Schema conference. Here, they talk about colour pairs, which I personally really like, and think it could be more widely used.

That was a lot of words. Let me know what you think!