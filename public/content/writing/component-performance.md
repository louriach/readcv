---
title: 💡Loose thoughts: Variants, nesting, and component performance in Figma
description: By Luis
---
When it comes to components, performance is incredibly important and there's a very common question when planning systems.

What's more performant?

1. A single (mega) variant

2. Nested and bubbled instances

![A comparison between a (mega) variant and a nested instance approach to building components.](/content/writing/component-performance-1.jpg)

### Let's analyse!

Here's what we're trying to achieve – an avatar component with:

1. 30 different avatar options

2. 3 shapes – circle, square, rectangle

3. 5 sizes – x small, small, medium, large, x large

In the single variant option, this ends up with **319 components**. In the bubbled instance we have **41 components** (30 options plus the variant options).

Immediately, we can see a maintenance win, but is it more performant? Let's take a look at the layers.

![A comparison of the numbers of layers between each approach.](/content/writing/component-performance-2.jpg)

For the Single variant – **5,120 layers**.\
For the nested instance approach – **4,482 layers**.

This is a nearly **15% increase** in size! It's worth thinking about this at scale within a file. With tonnes of instances in a file, you can imagine how this would bubble out into your file's performance at scale.

So that settles it! The nested instance approach is way more performant 🎉

### Wait there's more

I might have tricked you on this one. For the avatar component example, this is probably not the best way to build that specific component. Given it's a large list of images, it can be made way more performant with...styles!

![The layer size of a reduced component set, where you use styles for variation](/content/writing/component-performance-3.jpg)

Reducing the variant set down to the compositional changes – size and radius – allows you to offload the stylistic variations within the avatars to your styles. Each avatar can be created as a style, and your designers can swap them out!

### And there's even more

Variables! If your avatar is consolidated into a single shape with incremental radii as it gets larger/small – then you can use variable modes to reduce the component set even more.

![A video showing the variable setup for the hyper consolidated approach](/content/writing/component-performance-4.mov)

Of course, this is stylistically very different to the first options, but worth considering is consistency and performance are your ultimate goals!