---
title: Loose thoughts on versioning in Figma
description: By Luis
---
Versioning components is a tricky one. Versioning files (or designs) arguably even harder, especially with design artifacts increasing on a daily basis.

Figma is "always on", so does this mean that we shouldn't even try to version? Always live, all the time sounds fantastic and gone are the days of exports and imports and PNGs and PDFs and server storage, but we still have a big problem – maybe we *want* or *need* to freeze work.

When approaching versioning, it's useful to consider both sides of the collaborative equation – designers and developers.

Here are some useful questions to ask to establish some foundations before considering what level of versioning we might need:

**Design**

*Components*

1. Do you need to manage multiple component versions at the same time?

2. Do designers need to create work using multiple component versions?

3. Do designers need future versions of components before they are committed to handoff?

4. Do we want to version by component, by pattern, or by library?

*Screens*

1. Do we need a "source of truth" of our entire product / app / website? Be careful with an immediate "yes" here; some of the largest and most respected companies do *not* maintain large truth files

2. How long should a file last? Yes, this may be an impossible question to answer

3. Do we need to reference flows within flows? For example, a log in flow that's consistently referred to from within other larger flows. Again, likely yes

For screens organisation, it's worth checking out my file structure community file: [figma.com/community/file/1004041613962064465/file-structure-best-practice-guide](https://www.figma.com/community/file/1004041613962064465/file-structure-best-practice-guide).

For the "repeat flow" problem check this one out: [figma.com/community/file/1179022882729015433/repeat-flow-components](https://www.figma.com/community/file/1179022882729015433/repeat-flow-components)

I'll likely write another post about this, as it's a lengthy topic in itself.

**Development**

1. How do your developers version components?

2. How often do you release major/minor versions?

3. Do your Figma and code libraries differ in what components are available

4. Do you create components in Figma that you don’t need in code?

5. Do you create components in code that you don't need in Figma?

This is a lot of questions, but clarifying the answers should hopefully help provide some grounding for you to approach a solid versioning system.

### The contribution process

![Diagram showing a flow from design file to new feature to component library](/content/writing/figma-versioning-1.jpg)

Typically, we have our central design file which we then update with new features as they are prioritised. From here, we create new components for either efficiency gains or to live within the design system eventually. Then we move these components to the design system, and publish those out to the wider team.

This in theory works great! But in practice, we enter a world where we chase our tails trying to stay on top of component creation and contribution back to the system.

![A flowchart of the complicated process of multiple design files trying to contribute back to the design system all at the same time.](/content/writing/figma-versioning-2.jpg)

We therefore end up in a situation of constant creation, moving, publishing. In a small team, this is manageable, but as soon as we introduce different releases per team or timezone we end up in a world of pain.

Back to the topic, it makes versioning harder too. If my team needs to ship a feature that uses version 1, and your team needs to support version 2 because you're releasing much further in the future, how do we manage that with a single component in a single library?

As soon as we update the component to version 2 in our library and hit the publish button, every single designer is grandfathered into the newest version. This should be sending alarm bells to us all!

We need the ability to maintain two separate versions of the same component, but unfortunately this isn't possible within Figma **yet**.

As a result, we need to think laterally to figure out a solution for all.

### What options do we have?

**Option #1 – More components**

![Visual showing two components being published into a single design file. The first component has a label "version 1" and the second "version 2". There is an arrow pointing towards the "version 1" shape with a label reading "6 month deprecation plan".](/content/writing/figma-versioning-3.jpg)

It might sound counterintuitive, because of the live nature of Figma, but perhaps the easiest way to manage (major) component changes it to...make more components.

For minor updates to components, editing the same component may be just fine, but for larger structural or theming changes, it's probably best to isolate this change in a controlled way.

That might mean adding another variant to your component set, or a new component set entirely if the changes are significant.

*Pros*

1. You can independently manage versions of components, providing teams with the ability to switch to the newest version when they need to

2. Existing in progress work will not be disrupted with the newer version

*Cons*

1. It's perhaps inefficient to maintain components with the same in the same library. It could cause confusion for finding the correct version. To get around this, you could add the a label or word modifier to the new component, perhaps "future", adding an emoji to the end of the component name, or using the actual version number e.g. "Card v4"

**Option #2 – More design files**

![A flowchart showing a single component being updated twice. For each update, it is consumed within a different design file. There are design files named by quarter – Q1 2024, Q2 2024, Q3 2024. As each update of the component happens, it is pushed into a newer design file.](/content/writing/figma-versioning-4.jpg)

I raised the question earlier about how long design files should last for. This is, most of the time, an impossible question to answer because of course project lengths differ.

Centrally though, I believe we should strive for a world where design files are throwaway deliverables, versus an ongoing "forever file" that's constantly updated. I appreciate that in larger, more traditional industries, this is more like blue sky thinking than a worthy reality, but it's definitely worth striving for.

Once the work has been done, do we really need to refer back to that piece of work again if the production product is our source of truth? How often, realistically, are we going to be updating the entirety of that user flow? As the answer gets closer to "not that often", the higher the chance we can create new files for newer features.

With this method, there might be a scenario where you can create a new design (feature) file for each major piece of work you're creating. This could align with dates, for example Q1, Q2, Q3 etc. Or it could align with flows, for example "onboarding" or "settings". As we create more files, we can more easily inherit updated component versions too.

As our table component updates to version 4, our new(er) design file can inherit it without the concern that we're conflicting versions within a legacy design file that was created 2 years ago.

Smaller and more frequent files, less headaches.

```
A word of warning: if you use pages for versions, be mindful that as soon as you update the file with changes from your component library, every single component will be updated to the latest version. This will mean your versioned pages are all in fact now the latest version.
```

### **Option #3 – Staging libraries**

![A visual representation of the "production" and "staging" Figma library concept, showing a publishing flow from the two separate libraries into a single Figma file. The Figma file also contains a label for "local components".](/content/writing/figma-versioning-5.jpg)

This one is more likely to be possible with a larger product organisation that can't bet on small files being created for every piece of work.

There's a scenario where we want to contribute frequently to our system, but at the same time not move too far ahead what versions our developers are expecting. Designers typically work way ahead of time with new feature work compared to the designs the development team are implementing. Conflating these versions could be an expensive mistake!

With this in mind, we could introduce staging component libraries to help us stay ahead with future work, but without compromising the current state within our system.

A staging library is any components which aren't quite ready for production, but are ready to be used.

1. Future components, not ready for implementation

2. Newer major versions that you need to test in design files

3. Component tests that need to be isolated

4. A/B test components

Pulling these components into their own staging, or "sandbox" library will provide you with the flexibility or a system-wide publishing cycle, but protect your existing design flows and current component versions.

### <end>

That's all! Let me know what you think. This is possibly a work in progress article, as I formulate more thoughts on the topic.

\--

**Update 25 September 2024**

Ben Armstrong over on [LinkedIn](https://www.linkedin.com/feed/update/urn:li:activity:7242198881919283202?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7242198881919283202%2C7242505040538603520%29&dashCommentUrn=urn%3Ali%3Afsd_comment%3A%287242505040538603520%2Curn%3Ali%3Aactivity%3A7242198881919283202%29) shared how they set up their future components with a label of "experimental". I like it!

![Screenshot of the Figma component description field a description of a component that's currently experimental.](/content/writing/figma-versioning-6.png)