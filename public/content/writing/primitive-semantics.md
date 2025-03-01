---
title: A case for primitive semantics
description: By Luis
---
When building tokens in our systems, the rules are always:

1. Primitive variables (not published)

2. Semantic variables (published), with every semantic variable named with "intention"

Right? Well, maybe not.

![An alert component in success, error, and warning variants alongside a screenshot of a Figma variables panel showing a list of semantic colours.](/content/writing/primitive-semantics-1.jpg)

This logic works very well for most components and screens, until we start to work within systems that require a higher level of personalisation. This might be in data visualisation, or software where you need a huge list of colour choices, for example a colour-coded pill list that you might have seen in Notion.

How should we approach this? When thinking back to a classic naming convention system, with `bg-primary`, `bg-secondary` etc, how would we go about setting up this level of flexibility? I don’t think we can!

![A pie chart set in shades of blue, green, and purple.](/content/writing/primitive-semantics-2.jpg)

Instinctively, we might try to think through a logical and semantic naming system for something like a chart. `bg-slice` is where we might start. The second part of the chart? Mmm, `bg-slice-2`?

It doesn’t feel right, does it?

It’s at this point in naming conventions where we must juggle strictly aligning with a system and bending the rules to make discoverability easier, even if it feels wrong. Where it might feel wrong is introducing less semantic names within your collections to address these scenarios.

### **The primitive semantic**

Taking an example of something a bit closer to home, you’re probably familiar with the multiplayer cursors in Figma. These are a colour system in themselves, separate from the colours you may experience in other parts of the product.

![A laid out set of Figma cursors.](/content/writing/primitive-semantics-3.jpg)

Similar to the chart example before, how would we name these? `bg-cursor-1`? `bg-cursor-a`? Again, it doesn’t feel right.

So what do we do?

1. Publish primitive values?

2. Introduce a new token level?

3. Introduce non-semantic tokens to our semantic level?

![A label reading "primitive" and an arrow pointing to label "semantic". There's a separate arrow pointing from "primitive" to a label reading "something else?"](/content/writing/primitive-semantics-4.jpg)

At Figma, the multiplayer cursor tokens are stored within the semantic collection with primitive-ish names, which alias primitive values from a separate collection. These values are given a semantic start and a primitive end. For example, `multiplayerblue`, `multiplayerpurple`, `multiplayerred` etc.

This gives the benefit of not having to publish primitives, and means that `multiplayerblue` isn't fixed to a specific flavour of blue.

![The Figma cursors alongside a screenshot of the variables panel, showing the names for each cursor.](/content/writing/primitive-semantics-5.jpg)

There is an argument to suggest that we could pull these values out into their own separate variable collections called something like "decorative". This might be useful at a large scale where you have tonnes of detailed charts to work on.

The thing to consider here is that any new collection being introduced might put your modes at risk – how would you handle light/dark if you’re currently bundling those into the semantic collection? Perhaps your chart colours don’t differ in values across modes, in which case you will be fine.

If you go down the route of splitting these variables out into a separate collection, it might be worth considering an entirely separate *file*. The benefit here is that you would be able to publish and surface the variables specifically to whoever needs them, instead of it being available in every file within your account.

![A flow showing primitive going into semantic and separately into decorative, with semantic and decorative then flowing into a design file.](/content/writing/primitive-semantics-6.jpg)

This method essentially works for anything non-semantic or a "rule" deviation within your system. For example, your brand team need to create some illustrations and require a series of colours to support that. These could follow a similar principle – `illustration-yellow`, `illustration-grey` etc.

As a systems owner, you want to ensure the correct and approved variables are used, but it's way easier as a designer to use "yellow" than searching through a semantic but contextually challenging list.

Fixed primitives, flexible application.