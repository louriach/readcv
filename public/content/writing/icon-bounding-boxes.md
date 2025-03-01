---
title: Do we really need icon bounding boxes?
description: By Luis
---
There's something bugging me about icons.

Take a look at these two components, what's wrong? 10 points are on offer.

![Two light blue components with icons inside and a text string reading "label". The left component has a horizontal 3 dot icon, the right component has a vertical 3 dot icon.](/content/writing/icon-bounding-boxes-1.jpg)

That's right! There are two problems:

1. The left padding is optically too large

2. The gap is too loose

![Visual of the same two previous components, with a yellow annotation pointing to the issues described in the tweet](/content/writing/icon-bounding-boxes-2.jpg)

When composing components like this (with an icon), the process is:

1. Nest an icon

2. Set preferred instances

3. Bubble up the icon to the top level for instance swapping

![A visual showing the process of nesting an icon inside another component. It also shows two overrides to the icon, one showing the original horizontal three dot icon and the second showing the vertical 3 dots.](/content/writing/icon-bounding-boxes-3.jpg)

This is because of...bounding boxes.

They make sense because "consistency", but in practice introduce complications to consistent systems-oriented design.

What can be a perfectly set up grid of 24x24 icons in your system can create problems for pixel perfection in designs.

![A set of icons laid out on a black background. The icons are presented twice, once plainly and secondly with a red background and border. The previously used "more vertical" icons has a yellow arrow pointing towards the bounding box space with a label "gross".](/content/writing/icon-bounding-boxes-4.jpg)

We're then forced to create specific space overrides for when bounding boxes are too large. This is optical design running its course, but as a systems person you scratch your head because of the magic numbers requirement for "Left padding 8, right 16", as an example.

![A comparison of the problem icon within a bounding box and the solution – creating custom padding around the icon within the component..](/content/writing/icon-bounding-boxes-5.jpg)

What **is** useful is height. There's an argument to suggest a height-based bounding box could create consistent touch point size (for accessibility).

The likelihood for horizontal sizing is that your icon will always be nested, for example in an icon button with a width anyway.

This could mean that icons are sized with their inherent width in the system, versus a consistent X rule It would remove the need for pixel overrides, and mean that icons should "just work" when placed as instances It feels like scalability.

![Layout showing the proposal – horizontal bounding boxes are set to the width of the icon, not a consistent one. This means instances of both the horizontal and vertical three dot icons fit within the original component without manual spacing tweaks.](/content/writing/icon-bounding-boxes-6.jpg)

### **Other things to think about**

**Inheritance tax**

When setting fixed sizes at the icon level (within the system) we're kind of making future decisions without the context.

Should the icon button be the place we decide on the icon's size, versus inheriting a choice?

**What if we need a fixed size?**

![An annotation showing two illustrations horizontally. The left one has an icon button component selected in Figma, with a red arrow highlighting the width and height settings in auto layout, showing they are set to "hug contents". The right illustration shows outline mode within Figma, with the icon itself selected inside of the icon button. There's a red circle over the height and width settings, showing they are set to a fixed size.](/content/writing/icon-bounding-boxes-7.jpg)

Taking a common example, an icon button. The likelihood is that your component is set to a fixed (or minimum) size in order to meet tap target sizes for accessibility.

This is a specific instance where we need the icon at a perceived fixed size too. But is that true? Is the size not defined by the wrapping button element?

To protect optical sizing, we can manage this by wrapping the icon in a div (in HTML) or frame (in Figma) to manually set its vertical or horizontal position.

![An illustration showing an iconList component with a dotted pseudo bounding box.](/content/writing/icon-bounding-boxes-8.jpg)

This would be the same if we were looking at something like an icon list, as demonstrated in the above asset.

\--

This article will likely be ongoing.

Thanks!