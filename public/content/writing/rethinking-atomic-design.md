---
title: Loose thoughts: Rethinking atomic design
description: By Luis
---
![The atomic design process with a scribble through it](/content/writing/rethinking-atomic-design-1.jpg)

I think it might be time to reconsider whether atomic design helps or hinders the creation of designs and systems.

It’s been the de facto rule for looking at interfaces for a long time, but I find that sometimes it can actually create more confusion.

Atomic design is great! The issue we face though is that it’s best suited for frontend code architecture, and not necessarily within design files. It helped me understand the construction and component composability at a foundational level, but I want to flip the script a bit.

> Before we start, I’d encourage you to read the blog post if you haven’t yet: [https://bradfrost.com/blog/post/atomic-web-design](https://bradfrost.com/blog/post/atomic-web-design/).

### The structure

![The atomic design process](/content/writing/rethinking-atomic-design-2.jpg)

Until now, we’ve followed the “atomic structure”, with the proposal being:

1. Atoms – Singular components (button)

2. Molecules – Groups of atoms (input + button)

3. Organisms – Groups of molecules (menu)

4. Templates – Page layouts

5. Pages – Template instances, custom content

I find it breaking down for a few reasons:

1. An atom in HTML isn’t an atom in design

2. Atoms are way more flexible than their definition

3. Organisation within design tooling can be confusing

4. Translating “templates” into design implies components – not technically correct

### The challenge

An atom in HTML isn’t an atom in a design tool.

![A vertical side by side of a code block showing an HTML input field, and the same element but in Figma.](/content/writing/rethinking-atomic-design-3.jpg)

Call me particular, but an HTML input field in HTML is one thing, but in Figma at least two. We have the frame on the outside, and the text node inside. This is technically now a molecule, but we must convince ourselves it’s an atom.

Let’s say this input field now had an email icon.

![A vertical side by side showing an HTML input field with a <span> for an icon, alongside the Figma version](/content/writing/rethinking-atomic-design-4.jpg)

```
This is just one way of coding it, and there's probably a better way!
```

Is that two elements or three? In HTML it could be either, depending on whether you position the icon within the field using CSS or have it in the HTML.

The structure in design and dev is inherently different! As we strive for 1:1 design/code parity, our ambitions fall apart when think about these (simple) atomic use cases.

This then cascades down/up to our larger component sets and the concepts become harder to grapple with.

### Props

The more we think this through, the more challenges we find.

![A component and instance in Figma of an input field, alongside the properties panel. The panel is showing a boolean prop for toggling on/off an icon.](/content/writing/rethinking-atomic-design-5.jpg)

What about component props? There have been calls to include tokens/styles as a layer beneath atoms (subatomic, ions, quarks, etc) but a prop is a way to think about an "under layer" too. I'm confused.

Props can increase or decrease component contents, often changing an atom to a molecule, or a molecule to an organism. If we decide to ship the visibility on or off, we'd also be changing the composition of its atomic structure.

### Design tools

![A side by side "or" proposal for page structure in Figma. The left side showing an atom-based approach, the right showing a group system.](/content/writing/rethinking-atomic-design-6.jpg)

The organisation of assets within design tooling can be confusing.

I’m asked a lot about the best way to organise an atomic system and I don’t think there is one, because we gain little benefit from introducing atomic page/frame/section structure.

With this framing, it becomes more cumbersome to navigate, rather than structure aiding comprehension.

Is it more beneficial to group by intent, or by underlying atomic concept? I’d go for the former because of how you navigate elements within design tools.

Understanding the structure of a component does not equal how it is organised, and that’s totally fine!

### Templates

![A web design mocked up in Figma, presented as a component.](/content/writing/rethinking-atomic-design-7.jpg)

Translating “templates” into design implies components, which is not technically correct. I'm sure you've turned a full screen into a component for repeatability before!

I dream of a world where non-component templates can be built within design tools, a bit like a synced block in Notion, but we’re not there yet.

![3 identical web designs in Figma, but with different imagery.](/content/writing/rethinking-atomic-design-8.jpg)

It means that to follow the template workflow, all templates must be components, which disrupts the system.

### The proposal

Maybe I should propose something!

![Luis' proposal for simplyfing atomic design](/content/writing/rethinking-atomic-design-9.jpg)

I think we can simplify by flattening atoms, molecule, organism into a single “component”. Those component groups are then called “patterns”. Template is still tricky, but we need a term for full designs, hence “screen”.

As you can see, I haven't named this. Perhaps it doesn't need a name 🤔.

I do however, believe an acronym will work: **CPS**.

**C:** Components\
**P:** Patterns\
**S:** Screens

> Further reading
>
> This was also explored in Andrew Couldwell's book [designsystemfoundations.com](http://designsystemfoundations.com), where he proposed:
>
> 1. Screens
>
> 2. Features
>
> 3. Patterns
>
> 4. Components
>
> 5. Foundations

## **Where do tokens fit in?**

After publishing the original post, I received a few responses asking about tokens / variables and their proximity to the proposed system. I didn't include them originally for a few reasons, but most importantly:

1. Not everything is a component – this can be debated in a future post 😈

2. Tokens / variables have their own complexity when it comes to structure, organisation, syntax, and other developer-y things

![The CPS flow alongside the same flow but with tokens at the start. There is an arrow from left to right pointing from tokens into components.](/content/writing/rethinking-atomic-design-10.jpg)

Logically, we would insert tokens at the start of the flow. We have tokens, then components, then patterns, then screens...right? Well, not quite. Tokens flowing from the start would present us with TCPS:

**T:** Tokens\
**C:** Components\
**P:** Patterns\
**S:** Screens

The issue I immediately find is that tokens aren't **just** for components, they permeate entire products and websites, regardless of whether everything is a component or not.

![The CPS flow alongside the same flow but with tokens at the start. There is an arrow from left to right pointing from tokens into components.](/content/writing/rethinking-atomic-design-11.jpg)

This means that instead of a single TCPS acronym, we are presenting tokens as an **and**, versus alongside.

**T:** Tokens\
**and**\
**C:** Components\
**P:** Patterns\
**S:** Screens

We now have **T+CPS**. It looks like a scientific formula, I kind of like it.

### The split

The arrows imply that tokens always flow into a component, but we might want to consider splitting tokens out and feeding them into components, patterns, and screens independently.

![An example website screen for an ecommerce store, with an arrow pointing to its background color. Alongside the arrow is a label "Background/Primary". Underneath the label reads: (not a component).](/content/writing/rethinking-atomic-design-12.jpg)

An example: your body colour.

This isn't a component, and therefore doesn't fit into the CPS (components, patterns, screens) flow. Therefore, we need the mental model to shift and for tokens to sit outside of those guidelines.

> I will park the argument about surface vs background or default vs primary for the naming conventions here, this is more about what is or isn't a component!

The tokens for our page background, our containers, sections, or pretty much any HTML element that isn't set up as a repeatable component still needs to be stored and (re)used, and forcing ourselves into a "tokens are for components" mindset can trip us up later on.

### Functional and presentational tokens

Perhaps it's time to consider splitting out what we need on component-like elements, and what we need for non-components?

![❖ Functional tokens: components, and ☀ Presentational tokens: non-components.](/content/writing/rethinking-atomic-design-13.jpg)

This is why I'm opting to describe tokens as either:

1. ❖ Functional i.e. components

2. ☀ Presentational i.e. not for components

I'm still figuring the definitions out, but I think this makes sense to help aid the example I just shared. With this in mind, perhaps it's also time we interrogated how our aliasing system is structured to aid the two different (semantic) outputs.

As an example, would it be easier to iterate on screens and new components independently if we could use more tightly scoped tokens? The risk we always face with a more generic semantic token – for example, background-default –  is not having a wider view of the impact when you change its value. You might need a background-default that has is slightly darker for a specific use case. The temptation here might be to create a hyper specific component token, but what if it's not a component? I could ask questions all day here, but let's carry on.

![Mono/100 being split into a functional menu/background and a presentational screen/background.](/content/writing/rethinking-atomic-design-14.jpg)

A functional vs presentational split could look something like:

Primitive: Mono/100\
↪️ Menu/Background\
↪️ Screen/Background

Again, the naming conventions here are examples and are probably not great. However, menus and backgrounds make up a significant part of interfaces. Popover would be another good one, or card!

![Mono/100 being split into functional and presentational tokens for a menu, action, and screen.](/content/writing/rethinking-atomic-design-15.jpg)

Extending the logic, our primitive may be extended like this:

Primitive: Mono/100\
↪️ Menu/Background\
↪️ Action/Background\
↪️ Screen/Background

A simplification, but hopefully you are following the logic here.

### This sounds like duplication

Hang on, one primitive being split into 3 identical backgrounds, isn't that inefficient? Yes and no.

I'd wager that it's faster and easier to build a muscle memory for searching "*action-background*" than wrestling the cognitive arm of "does *background-default* mean white, or that light grey that we use, or is default something we shouldn't be using a lot?".

A generic, widely applicable token system is the dream-state, but I'm not sure we can get there in organisations that aren't very tightly intertwined. Additionally, for the scenario where you *do* need to use a light grey instead of a white, would you instinctively know that you should be applying (for example) *background-secondary*? Or is it *background-tertiary* because that's how you've split lightness within colour ramps? I don't know, and your design team likely don't either.

It's way easier to search for a **component** *background-action* or a **presentational** *background-page* than to remember that there is one token to rule them all. This supports the ability to iterate and test new concepts faster too.

Let me know what you think!

### Canonical

This was originally posted as two threads:

1. [Atomic design](https://x.com/disco_lu/status/1654479672984457217)

2. [Atomic design and tokens](https://x.com/disco_lu/status/1658475897811517442)