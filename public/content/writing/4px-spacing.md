---
title: Loose thoughts: Saying bye to 4px spacing and hello to Fibonacci
description: By Luis
---
I have a consistent routine when I work with a new designer. I head to Google, search "8px grid Medium.com", pull up Elliot Dahl's comprehensive guide and send it to them. Here's the guide: <https://medium.com/built-to-adapt/intro-to-the-8-point-grid-system-d2573cde8632>.

This guide is fantastic, and would highly recommend. I have, until this year, treated multiples of 4 (not 8!) as practically my design bible. New element? Surely the left padding is 16, the top is 12? Every...single...time.

![A pill component with labels pointing to the padding values. The left and right padding is 16, the top and bottom is 12.](/content/writing/4px-spacing-1.jpg)

Whilst this approach to designing can help with predictability, and becomes muscle memory for setting components up really quickly, I can't help but think we've ran ourselves into a world where unfortunately everything looks the same.

### Odd numbers

![A comparison between a pill component set with even numnbers for padding against one that has been set with odd numbers.](/content/writing/4px-spacing-2.png)

Perhaps it might be worth us considering using odd numbers for spacing instead of even, in order to shake things up and keep us all sane.

```
I'm prepared to go to grid system jail.
```

The issue I have with the even number 4px calculation grid systems is that they can feel a bit loose, either vertically or horizontally. Although this is the de facto standard in product design now, I find myself getting focussing on what feels like a few pixels of extra flab within our components.

### Comparing

![The same comparison of pill components using either the traditional spacing logic, or the odd one, but with their padding values overlaid on top.](/content/writing/4px-spacing-3.jpg)

Let's look at a comparison. On the left of the above image we have the traditionally spaced components in their 4px system. On the right, we're tweaking to be odd numbers. Personally, they **feel** better. What do you think?

What I've done here, is tweaked things manually up or down by a pixel or two in order to refine the padding to feel tighter. This stands out particularly well in the second and fourth pills from the top, where when comparing you can see that the odd number approach feels way more consistently padded.

### What about fonts?

The first pushback against this idea may come from the difference in how fonts would disrupt the spacing because of their inherit sizes.

Let's take a look!

![A comparison of 6 fonts using the 4px system or the odd system: Oxygen Mono, Noto Serif, Roboto, Poppins, Palatino, Koulen.](/content/writing/4px-spacing-4.jpg)

Interesting! There is little difference in how things feel. You still get the same tighter end result on the odd spacing whether it's a mono or serif font.

What is important to note here is that line height would have an impact on how this all comes together. This works fine for single line text, set at 100% line height, but for larger areas of copy we would need to experiment.

> Important
>
> Within these pills, all of the font sizes and icons were set to an even size! So perhaps the combination of even inner and odd outer can provide us with harmony.

### In the wild

![Screenshot of the Notion Mail landing page hero, with annotations on top of the form showing their pixel perfection.](/content/writing/4px-spacing-5.jpg)

I came across Notions approach to this recently whilst looking at their new [mail landing page](https://www.notion.so/product/mail).

They have approached this by mixing even and odd numbers to great effect. They have fine tuned the padding of the button to be odd numbers for *feel*, but then used the classic border radius calculation to have fine tuned but calculated radii for the inner and outer elements.

### Systematising it – Introducing Fibonacci

![A comparison of the 4px grid system against the Fibonacci scale.](/content/writing/4px-spacing-6.jpg)

If I were to try and roll this idea out into a system, I'd probably want to at least try to build in a method to the madness. This is where we can lean on systems like the Fibonacci sequence to handle the heavy lifting.

![The 4px grid.](/content/writing/4px-spacing-7.jpg)

In the 4px system, we space like this – A base unit of 4, then multiple it by 1 (or x.5 if we're being funky) to get our system:

1. 2 (0.5x)

2. 4 (base)

3. 8 (2x)

4. 12 (3x)

5. 16 (4x)

6. 20 (5x)

7. 24 (6x)

8. etc

But the Fibonacci system would work by adding the two previous values together.

![The Fibonacci spacing system.](/content/writing/4px-spacing-8.jpg)

1. 1

2. 2

3. 3

4. 5

5. 8

6. 13

7. 21

8. etc

Like we discovered earlier, it's definitely...odd, but there's something here I like.

![A comparison of the 4px grid system versus the Fibonacci one, using a slider.](/content/writing/4px-spacing-9.gif)

When comparing the systems on an example component, the differences are minor, but isn't that what we're here for? That's a rhetorical question 🤣

### Further reading

Some very clever folk in the industry have made tools I'd recommend checking out:

1. <https://utopia.fyi/>

2. <https://symbols.app/docs/sequence>

3. <https://proportio.app/>

\~

This was originally posted as two separate [threads](https://x.com/disco_lu/status/1653395731451969537) over on [Twitter](https://x.com/disco_lu/status/1759641396846239795).