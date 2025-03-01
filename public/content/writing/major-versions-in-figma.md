---
title: Loose thoughts: Managing major versions in Figma design systems
description: By Luis
---
With every change to a variable, style, or component, we must anticipate the downstream impact to a design file that is already consuming it.

If we reorder the elements within a component or change its visual appearance during the time at which a feature is being developed, we may disrupt the "handoff" process significantly, impacting the development costs and planned estimation time for build.

\-

A major version changes (in Figma) can happen in a bunch of different situations, here are a few:

1. A rebranding

2. A significant restructuring, with either styles or components

3. Naming convention changes

4. Keeping up with feature releases, for example changing from styles to variables for color

5. Asset locations are changing e.g. one component moves to a new library with different permissions / access levels

And a quick summary of each:

1. **Rebranding**

Significant visual identity change will impact color contrast, spacing, typography, and often impacts component structure too.

2. **Significant restructuring**

This is related to, but also separate from rebranding.

A visual refresh of a page within the same brand guidelines will often change how a component is architected, and therefore downstream changes in any instance of the previous component will break or change the layout considerably.

3. **Naming convention changes**

A pretty straightforward one! *Card* may become *Tile*, *Card* may become *Card – Product* etc.

4. **Updating for feature releases**

Variables are the most recent significant update here, but previous releases included component properties, or variants.

5. **Asset location change**

This one comes with an asterisk, because it's unlikely to happen but is worth bearing in mind. If you move a component to a library with different user permissions, consumers may lose *or* gain access.

\--

### **Friction**

There will need to be friction introduced with a change like this. I repeat, **need**.

A question we must ask ourselves is *where* we want this friction to occur.

**Another important thing to think about**

We need to know whether the business has a requirement to support concurrent versions.

* Does one team work on version 1 and another version 2?

* How do we plan to manage this?

Here are a few options to think through for mitigating this friction:

**Option 1: Friction for the library**

When playing out the idea of a major version introduction, there are a few options for components:

1. A new variant within the same component

2. A new component

3. An entirely new library

The severity of change here increases as we go from 1 to 3, but the control increases too. In order to make a decision about which option we might want to investigate, we need to know if this major change is affecting just a single component, or the entire library. AKA, do we version individually, or as a whole?

1. A new variant

A new variant within the same component is pretty simple to manage at an atomic level, but as soon as we introduce that new version into a larger pattern which *aligns to a previous version*, we are packing our bags and moving to Trouble Town, Ohio.

![An accordion item variant component which has had a new variant added, styled differently. Underneath the accordion item is an accordion, which has the item nested inside.](/content/writing/major-versions-in-figma-1.jpg)

It's this fragility which could make or break a rollout.

2. A new component

![A "current" accordion item component alongside a "future" version, which has a different visual treatment. Below is a full accordion component, with the open accordion item selected, alongside a screenshot of the Figma properties panel instance swapper. In here, you can see there are two accordion items listed: the current and future versions.](/content/writing/major-versions-in-figma-2.jpg)

A new, replacement component provides you with the ability to split versions and provide a longer term deprecation / rollout. I might write about this in a different article.

Perhaps we create a new component, and add a suffix of "– Future", to indicate to consumers that it's coming soon.

The word "future" is TBC but right now it makes sense to me as a way to detach from a fixed version number, but to indicate it is *new*.

3. A new library

An entirely new library is a drastic change, and probably best served as part of a brand refresh where the entire visual direction is changing for every consuming design file too. I like this option though!

**Option 2: Friction for the design files**

Some design teams use files as throwaway artifacts – once a piece of work is finished, the file is retired.

Some design teams maintain single files forever, with ongoing overrides to existing assets, a branching workflow for managing changes, or a new page for each version.

`🚨 If you use pages for versions, bear in mind that each time you inherit a library update, your file will be automatically updated to the latest. This will overwrite your pseudo versions and will give you a headache.`

Try to be the former! Files could, and possibly should, be snapshots in time, with our production product acting as the truth and not a file with 10,000 frames.

(I was speaking to a designer at a very popular code repository management tool recently who told me that their files are often literal screenshots of the production app and designers draw over the top to create new features. I didn't tell you that 🤫)

**Inherited versions**

If we overwrite our components to upgrade their versions, and then embed these as instances in a larger pattern, we run the risk of inheriting a version before we're ready.

Take the image below showing an *accordion* item's visual appearance changing, and then being nested into an *accordion* component. Does *accordion* automatically become version 2 as well?  Or are we working with mixed versions? A question to discuss.

![An accordion item and an arrow showing it embedded in an accordion, presented vertically. Both of these have a label above them reading "version 1". This is repeated on the right side of the image, but the accordion item has been changed visually, and the label reads "version 2". The accordion underneath this one still reads "version 1", with a red circle around that label.](/content/writing/major-versions-in-figma-3.jpg)

**The choice**

The preferred route here is option 1 (friction in the system), even though it's your systems life which will incur said pain. Why? Because there are less people affected by the changes within the systems team compared to the amount of consumers of it.