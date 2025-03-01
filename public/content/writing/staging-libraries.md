---
title: Loose thoughts: Staging component libraries
description: By Luis
---
Let me paint a picture.

You’re designing a new feature, a very shiny one, and you are creating components specifically for this new piece of work. Nothing out of the ordinary here! You then make a new file and need to use an instance of these components.

Hmm.

The work has also not been coded yet, meaning that these components don’t technically live inside the design system yet.

Double hmm.

**What should we do?**

Logic states that a component used in more than one file should be in a published library. I like logic! But, with the high chance of developer confusion from a “not quite ready” component – a lack of documentation, accessibility checks, proper naming conventions, correct token usage – being pushed through to production, and goals of a robust contribution model within the design system, we run into a wall pretty quickly where our brand new components live in *layer limbo*.

### **Solution #1 – No components**

One could argue that a component is a system-level decision, only created once we have full sign off on designs and they are ready to be built.

The argument stands, but anyone that’s spent longer than 30 seconds designing something knows how much more efficient we can be when we use components and instances. When designing, I try to *start* with components. Propagating changes to many instances and screens can save a tonne of time.

Yet there is still the useful framing of Figma as a place to ideate, not formulate. The canvas is the best place for freeform thinking, where we’re not limited by fixed variables, styles, or previous component decisions.

Does this design require a slightly different take on the search field? Overriding the existing library component may cause more harm than good, so creating a brand new frame styled the way you need might help to push the needle.

Keeping your layers and frames in a non-component state also helps you to keep a Work in Progress mindset, both when designing but also presenting your work to colleagues.

It sounds good, but we still have the large inefficiency problem of having to them retrospectively turn everything into a component once your designs *have* been signed off. This could take hours for a large project.

Not so scaleable.

### **Solution #2 – Naming conventions**

Okay, so we still need components. The challenge we have though is communicating both to designers and developers that your components are either:

1. For design efficiency only

2. New to the system

**For design efficiency**

It’s a very common scenario when designing that you will need a component just for that piece of work. An example might be a list of items. In code, your developers will probably be passing data into a single list item, and the amount of items will be determined by how much data there is. On the design side, we have to be a bit more explicit with the amount of items, and a component makes this so much easier to manage.

![A list item component inserted into a larger list.](/content/writing/staging-libraries-1.jpg)

The challenge we have though is that we don’t want these to be coded, because their existence is purely to make designer’s lives easier. This is where we can use naming conventions and canvas organisation to communicate this.

Here’s my recommendation:

1. Create a page in your design file called **❖ Local components**

2. Create a section on this page for each component group e.g. **Search List**

3. Give this section a background color that isn’t white or dark grey, so it is presented differently in the assets panel. A light orange might work as a way to notify, but not alarm

4. Append each component with the label “– 🚨 **LOCAL**”

This is easier with a visual! See below:

![A Section in Figma with a local component inside.](/content/writing/staging-libraries-2.jpg)

And the assets panel:

![The Figma assets panel showing a component set on top of a light orange background.](/content/writing/staging-libraries-3.jpg)

This is great, but we still have the problem of not being able to use this component in another file. We don’t want to turn this design file into *another* library file – we need another solution. This will be covered in solution 3.

**New components**

For a new component that we do want to code and push into the main library, it must go through a contribution model back into our design libraries, but this introduces a potentially disruptive workflow for anyone in the systems team managing the library and also those on the consumption side.

We can’t be constantly adding and publishing work from the library, it’ll cause planning issues for maintainers and update blindness for consumers. This is a pretty common scenario I see in newer teams, and I like to call it the good-ol’-fashion-component-tail-chasing. It’s catchy. The alternative name is the *component ouroboros*, which is a lot easier to remember.

Anyway, we need to keep efficiency high and prevent adding bottlenecks to the design team who want to move their tickets from *in progress* to *ready for review*.

**Solution #3 – Staging libraries**

When building components in a new design that need to be pushed back into a main library and eventually coded up, the immediate thinking probably “let’s cut and paste the component into the main library and publish!”. This makes sense on the surface, but unfortunately falls apart quickly when you are running multiple concurrent versions of designs, or you need to prevent certain components from being available to the entire team.

This is pretty common in a workplace where you run frequent A/B tests, or have a very healthy culture of iteration and experimentation via components and need to have a situation where *Feature A* gets *Component A* and *Feature B* shouldn’t know it exists.

A way around this is what I call **Staging Libraries**. These are *additional* design system libraries in Figma, where your specific team, feature, squad, whatever can create what is in effect an extension of the system for your specific piece of work.

![Two Figma file thumbnails, one for a staging library and the other for a production library.](/content/writing/staging-libraries-4.jpg)

Taking our list item component from before, we would cut and paste this out of our single design file and into the design library that is local to our piece of work or team. This provides us the benefit of being able to access more components in more files, whilst also not muddying the main design system library file and confusing maintainers and consumers.

![The same thumbnails are before, but with an arrow pointing from the staging library to the production library, there is a label underneath reading "contribution to main system when ready for production".](/content/writing/staging-libraries-5.jpg)

The additional benefit of this staging library is that, like a staging server in code, it can be messier! We don’t need to be concerned with organisation, robust documentation, or even naming conventions. As it is staging and not production quality, it’s a way to ensure high efficiency whilst the high standards of the main system can be saved for later, perhaps when this component does indeed need to be global.

### Component progression and library tiers

Another way of looking at component location is in *tiers*. We start at tier 3 with our local components, and they are likely to be pushed into tier 2 (staging), and ultimately land in tier 1 (production library).

![A visual representation of the 3 component tiers.](/content/writing/staging-libraries-6.jpg)

This should help frame or decide where a component should live based on where it needs to be used and whether it should be pushed to production yet or not.

See you next time!