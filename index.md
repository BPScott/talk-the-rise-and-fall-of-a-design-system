---
title: The rise and fall of a design system
theme: sky
---

# The rise and fall of a design system

<small>Ben Scott / [@BPScott](http://twitter.com/BPScott)</small>

---

## Who

- Senior Web Developer @ Shopify
- Not from around here
- Favourite new Canadian word: gongshow

Notes:

Hi I'm Ben, I'm a Senior developer at Shopify where I work on their Polaris
design system, recently I've integrated Storybook and am currently helping write
tools to audit how we consume iconography.

As you might be able to tell from my accent I'm not from around here - I moved
to BC from the UK just over a year ago, and this talk is going to be about some
of my experiences at prior my employer back in London.

---

## Rewind

- bbc.co.uk/programmes circa 2013-2017
- Two component libraries for two visual redesigns
- The first went well
- The second didn't go so well

Notes:

From 2013 till late 2017 I worked at the BBC on their /programmes site. They're
the permanant digital archive for every TV and Radio show that the BBC has
produced in the decade. Name a TV or Radio show and there shall be a webpage
there that says when it was aired, who stared in it an what music was played. I
initially started as a developer on the team, and eventually became the team's
technical lead.

During this time we had two visual redesigns, which resulted in two distinct
component libraries, both of which I helped architect and evangelise. I consider
the first successful, but the second faced several issues and ultimatly I feel
it failed to live up to its intent. Now that the dust has settled and with the
benfit of hindsight I can pick out the good and bad and hopefully idenfify some
warning signs you should watch out for.

But first let's quickly talk about the deliverables of a design sytem. In my
head "implementing a design system" is very broad topic and can be split into
three deliverables.

---

## Design Systems

- Standardise patterns
- Are implementation agnostic

Notes:

In my head a design system itself is quite etheral. It is your rules and names
and patterns, written in a document somewhere. It sits above any code that you
write.

Patterns are the design token level things like "Purple is this specific color"
and "base font size is this pixel value", through simple visual concepts like "a
button looks like this" and including more complex domain object like a TV
programme that containd a title, synopsis and preview image.

Because of this abstract nature a single design system can be implemented in
multiple ways - in HTML for the web, in android and in iOS applications. If that
is the case your system shall probably have something to say about how to
integrate environment-level conventions like "buttons should look like the OS
buttons in native apps".

Once you have these common ideas you then write them into your application.

---

## Component Libraries

Notes:

That implementation within your application can take several forms - you could
be writing css and html fragments but these days there's a decent chance you're
leveraging a library that pushes you towards a component-based architecture like
React or Vue anyway.

---

## Styleguides

Notes:

You'll also want somewhere to document these components so that other members of
your team can view them so they know what exists - your Styleguide is how you
visualise and demonstrate all the tools in your toolbox. You could leverage an
existing tool like Storybook but its also fine to create your own corner of your
application to showcase examples of components and provide documentation on how
to use them.

Putting those all together you get:

---

## Design Systems

are implemented by

## Component Libraries

which are documented within

## Styleguides

Notes:

Your Design System is implemented by your Component Library - or possibly many
component libraries if you're building for multiple platforms - which is in turn
documented by your Styleguide.

For both of our projects, we were a team of 3 to 4 developers with occasional
input from a designer, so we mostly focused on extracting components out of
designs provided and from our understanding of the existing codebase.

---

## 2013 System

- Just /programmes
- In-app component library
- In-app styleguide

Notes:

The process for our first redesign went really well.

---

## Vision versus Manpower

Notes:

---

Ongoing Maintenance

Notes:

---

# Thank You

### Any Questions?

<small>Ben Scott / <a href="http://twitter.com/BPScott">@BPScott</a></small>

<small><a href="http://www.reload.me.uk/talk-the-rise-and-fall-of-a-design-system">reload.me.uk/talk-the-rise-and-fall-of-a-design-system</a></small>
