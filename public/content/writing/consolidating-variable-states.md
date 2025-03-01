---
title: Thinking out loud: Variables – Consolidating states
description: By Luis
---
## An idea 💡

![](/content/writing/consolidating-variable-states-1.png)

If your hover states are consistently within the same colour range e.g. adding 30% black to \*anything\* that is hovered, then instead of creating variables for every single variable's hover state, you create a single ––hover variable and use it within a composite style.

### With a card and tab example

![](/content/writing/consolidating-variable-states-2.jpg)

Where it quickly falls apart is if your colour adjustments are more manual, or if your colours don't fall within the same visual range.

My initial palette differed wildly, meaning that manual adjustments were a requirement.

You could have several composite hover **rules** though 🧐

![](/content/writing/consolidating-variable-states-3.jpg)

If anything, this approach it can highlight the differences in your colours. If you can bring your colours all within the same saturation range, this idea would work.

### Further thoughts

Thinking about this a bit more, I don't think a specific --hover variable is needed, it might be too specific to that interaction.

If your system uses a single mode (light / dark), then you could get away with something like this:

`––darken-interactive` \
`––darken-subtle` \
`––darken-strong` \
`––lighten-interactive` \
`––lighten-subtle` \
`––lighten-strong` \
`––brand-subtle` \
`––brand-strong` \
`––accent-subtle` \
`––accent-strong`

![](/content/writing/consolidating-variable-states-4.jpg)

It introduces two groups into the variable structure:

1. Modifier – System: This is where you store the fixed darken / lighten variables \\
2. Modifier – Brand: Any brand coloured tints you might need

They are both offered in subtle, interactive (for the previous hover), and strong.

If you are using multi modes (light **and** dark), then abstracting the names out will probably work.

So instead of lighten/dark – because they don't make sense in the other mode – we use `--overlay` and change the values in each mode.

![](/content/writing/consolidating-variable-states-5.jpg)

But what about when we need `black 6%` to always be `black 6%`?

This would likely call for a fixed variable value across modes, so we'd get:

`––overlay-fixed-dark-subtle`\
`––overlay-fixed-dark-strong`\
`––overlay-fixed-light-subtle`\
`––overlay-fixed-light-strong`

![](/content/writing/consolidating-variable-states-6.jpg)

Let me know what you think!