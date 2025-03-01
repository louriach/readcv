---
title: Loose thoughts: Typography variables structure
description: By Luis
---
Having played around with typography variables *quite a lot*, here's some structure advice!

Set up two collections:

1. Typography primitives

2. Typography

Number 1 will save you a tonne of time later on because of how efficient aliasing can be.

### Typography primitives

![Showing the Figma interface for a "typography primitives" variables collection](/content/writing/typography-variables-structure-1.jpg)

Within the **Typography Primitives** collection, set up variables for your system's font families. The easiest naming convention here is to follow the font type e.g. *Font Sans*, *Font Serif*, and *Font Mono*.

**Font scale**

![A screenshot of the font scale group within the typography primitives collection](/content/writing/typography-variables-structure-2.jpg)

Additionally, within this collection, create variables for font *Scale*. These match your lower and upper limit font sizes, which will be defined by how your brand is set up.

Scale here is a useful more generic word compared to size, which also won't confuse size within your larger system. For example, a small or large component may be confused with your type primitives. This also aligns a lot closer to font size scale factors e.g. golden ratio.

> Scale will typically match a calculation-based system in your code setup (usually REMs in CSS). A bit more info about this can be found over on [CSS Tricks](https://css-tricks.com/almanac/properties/f/font-size/). There are many different units for fonts, but that's a rabbit hole for another time.

You may need 3, 5, 10...100 variables for your scale, depending on how wide your system goes. Do you have mobile / web / tv? This will increase the amount of variables that you need to support here, but you can see the power of supporting many different outputs from a single primitive collection.

**Font weight**

![Screenshot of the Figma variables panel showing a Font Weight group within a collection](/content/writing/typography-variables-structure-3.jpg)

Within Typography Primitives, I advise including *Font Weight* variables too.

The easiest way to look at this is that you will need:

1. Number variables for weight e.g. 100, 200, 300. This matches the CSS number scale, more information over on [Mozilla](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-weight)

2. String variables for style e.g. italic, bold, oblique

This is confusing to begin with, because font weights work with both number and string variables! Additionally, Figma works differently to CSS.

In CSS, you can write:

```
p {
    font-style: italic;
    font-weight: bold;
}
```

However, in Figma, these are a *single field*. This presents us with a decision and/or a challenge – we **can't** write *700 italic* as a single number variable, but we **can** write *Bold Italic* as a string variable.

Hopefully this helps when trying to plan out what variables you will need to create for your text styles.

But wait! There is one more thing. Not every font sets up their font weights and styles in the same way, meaning *Semi Bold* in Inter, is actually *SemiBold* in Roboto 🤯. This means we would need to create two variables.

> This is explored more in my community file [Typography variables: System fonts boilerplate](https://www.figma.com/community/file/1364979538897082048).

### Typography collection

**Font groups**

![The typography collection, showing groups for each font style](/content/writing/typography-variables-structure-4.jpg)

For efficiency, in the main *typography* collection we create groups for each of our composed styles – for every *text style*, we create a variable group.

This looks like duplication, but will save you a lot of time later on. I promise! We can alias each primitive that we created earlier into these more semantic variables.

This is beneficial in a few ways:

1. If the brand sans serif font changes, instead of altering every single text style's definition, we change a single primitive

2. If a style's size needs to change, we remap to a variable within its group, or change the primitive scale value. This reduces the need to change individual style values, which in a large system may be out of your hands

![The variables collection and corresponding type styles. There are arrows pointing from the variables into the type style that uses them](/content/writing/typography-variables-structure-5.jpg)

With this approach, our variables are piped straight into the text style! We outsource the heavy lifting to the variables panel, and the type style becomes the user-facing end result.

![A swatch style layout for 3 type styles, showing how their variables are used for their values.](/content/writing/typography-variables-structure-6.jpg)

This is all explored in the [Simple Design System](https://www.figma.com/community/file/1380235722331273046) kit, available on the Figma community too.

See you next time 👋

\--

\~ [Original Tweet thread](https://x.com/disco_lu/status/1816860352090636555) \~