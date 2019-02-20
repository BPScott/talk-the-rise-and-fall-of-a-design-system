---
title: The rise and fall of a design system
theme: serif
revealOptions:
  width: 1024
  height: 768
  maxScale: 2
  controls: true
  progress: true
  history: true
  center: true
  transition: none
  backgroundTransition: none
---

# The Rise & Fall<br>of a Design System

Ben Scott / [@BPScott](http://twitter.com/BPScott)

---

## Who

- Senior Web Developer @ Shopify
- Not from around here
- Favourite new Canadian word: gongshow

Notes:

Hi I'm Ben, I'm a Senior developer at Shopify where I work on their Polaris
design system, recently I've integrated Storybook into our workflow and am
currently helping improve our tooling around how we consume iconography.

As you might be able to tell from my accent I'm not from around here - I moved
to BC from the UK a little over a year ago, and this talk is going to be about
some of my experiences at my prior employer back in London.

---

## Rewind

- bbc.co.uk/programmes circa 2013-2018
- Two component libraries for two visual redesigns
- The first went well
- The second didn't go so well

Notes:

From 2013 till early 2018 I worked at the BBC on their /programmes site. They're
the permanent digital archive for every TV and Radio show that the BBC has
produced in the past decade. Name a TV or Radio show and there shall be a
webpage there that says when it was aired, who stared in it and what music was
played. I initially started as a developer on the team, and eventually became
the team's technical lead.

During that time we had two visual redesigns, which resulted in two distinct
component libraries, both of which I helped architect and evangelise. I consider
the first successful, but the second faced several issues and ultimately I feel
it failed to live up to its intent. Now that the dust has settled and with the
benefit of hindsight I can pick out the good and bad and hopefully identify some
warning signs you should watch out for.

But first let's quickly talk about the deliverables of a design system. In my
head "implementing a design system" is very wide topic and can be broadly split
into three areas.

---

## Design Systems

- Standardise patterns
- Are implementation agnostic

Notes:

In my head a design system itself is quite ethereal. It is your rules and names
and patterns, written in a document somewhere. It sits above any code that you
write.

Patterns are the design token level things like "Purple is this specific hex
code" and "our base font size is this pixel value", through simple visual
concepts like "a button looks like this" and including more complex domain
object like a representation of a TV programme that contains a title, synopsis
and preview image.

Because of this abstract nature a single design system can be implemented in
multiple ways - in HTML for the web, in android and in iOS applications. If that
is the case your system shall probably have something to say about how to
integrate environment-level conventions like "buttons should look like the OS
buttons in native apps".

At no point here doe have any code, that comes at the next tiers where you start
writing these common ideas into your application.

---

## Component Libraries

Notes:

That implementation within your application can take several forms - for the web
you could be writing css and html fragments but these days there's a decent
chance you're leveraging a library that pushes you towards a component-based
architecture like React or Vue anyway.

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
component libraries if you're building for multiple platforms or have multiple
teams working on slightly different aspects of a larger product - which is in
turn documented by a Styleguide.

With those deliverables in mind lets go back to our implementations at the BBC,
and look at some of the ways the projects differed, how we approached those
differences and how that impacted their success.

---

## Back to the BBC

- 2013
- Amen

Notes:

Our two projects: the 2013 redesign - so named retroactively because we just
called it "the redesign" at the time as there was only one, and Amen named
because in 2016 we figured we needed that this time we needed a proper codename.

Both of our projects followed the BBC's usual design process of UX designers
producing high fidelity page designs which are the implemented by a team of
developers. It is then the developers job to identify the reusable components
within the pages designs, then create them - as part of the library - and then
to create a styleguide to document them for future use.

I wouldn't necessarily recommend that waterfally process of handing over a
completed artifact from design to dev in your projects but that was a very
deeply ingrained way of working at the BBC and we weren't in a position to
challenge that.

While that style of working remained similar for both our projects, the scope of
the work differed and in retrospect I feel we underestimated and failed to
respect that difference and thats what ultimately lead to my dissatisfaction
with the Amen project.

---

## Vision versus Manpower

### <br><br>

Notes:

In our 2013 redesign we were building components for a single application -
bbc.co.uk/programmes that was built by a single team within a single repository.
We were the developers for both the app, and the components to be used therein.
This constrained vision made for a straightforward build process. We built the
component library and the styleguide directly into the application we were
working on because we knew we didn't have to worry about external usage. This
was a small vision that fit the size of our team and all of our work fit our
existing remit of "work on /programmes", because of this we were able to
effectively execute.

For the Amen redesign we had a grander vision - the powers that be wanted to
create visual consistency across a pair of sister applications - /programmes and
/radio. So we said we'd create a shared component library that could be
installed in both applications via a package manager and it would be maintained
equally by both the /programmes and /radio development teams. We knew this would
be more complex than our prior success with the 2013 system but we assumed that
with both teams working along side each other we'd be able to deliver.

---

## Vision versus Manpower

### Match your vision to<br> your ability to execute

Notes:

However it turns out that wasn't a linear increase in complexity. By introducing
something shared between teams we now had to consider how to manage that shared
usage. We had to consider new concerns like versioning numbers, how to handle
backwards incompatible changes and how to deal with variations of a component
that would only be used in a single app.

We proclaimed that both teams would take equal responsibility for these new
concerns and that when building components they would be empathic of the other
team - by ensuring they build something that could be used by both teams and
providing documentation for that usage. However this didn't end up being the
case.

I underestimated the amount of additional effort required to make this a
reality. I assumed this time could be factored into the default time it takes to
build a component without much impact. Product management of both applications
were initially on board with this idea, however when this effort became a
greater burden than expected they considered it disposable and told us to focus
on what was required for their single application at the expense of creating
something sharable.

That change in focus is fine and completely within their right but be aware that
people responsible for an product shall tend towards what is most expedient for
their product, rather than what is best for the collaborative system in the long
term. Without a dedicated team to work on the shared components we were unable
to create the space for it to live up to its vision. Our vision was grander than
what we could accomplish given amount of time and manpower afforded to us.

---

## Burden of Education

### <br>

Notes:

This difference in our vision and our ability to execute was particularly stark
regarding education and sharing of information about the components.

In the 2013 system our work was contained within a single codebase maintained by
a four-person team. This smallness meant we could get away with less stringent
written documentation and rely on oral tradition for sharing information -
swivelling your chair and asking the person next to you to provide context on
why something was done in a particular way. Our styleguide still existed and
provided examples what a component and its variants would look like but we could
get away with not writing in-depth usage instructions, and instead we spent that
time focused on app build out. This worked really well for our team of four as
everybody was able to get up to speed quickly and new information could be
quickly passed around, and we didn't need to spend time on documentation that
wasn't needed because everybody already knew how things worked and we didn't
need to onboard new people.

In the Amen system however the scope of being used by two dev teams - around 12
devs overall meant that oral tradition wouldn't really work - interrupting a
member of your own team is fine, but you're a probably little more reticent to
ask someone external. There was also now twice as many people to onboard onto
the project which if you're onboarding by talking to people eats a lot of time.
At this scale written "getting started" documentation became important as we
didn't want developers familiar with the system explaining the same concepts
multiple times. I love mentoring but my product owner would have had some raised
eyebrows if I spent all my time helping the /radio team instead of working on
/programmes.

---

## Burden of Education

### Oral tradition does not scale

Notes:

Once again I dropped the ball. The /radio team were unfamiliar with the process
of using a component library and I and the other lead developer of the initial
system were unable to make time to fully explain the architecture choices we
made early in the development of the project, and to assist the /radio team as
they took their first steps into creating their own components due to our other
commitments within the /programmes team. We made an attempt at written
documentation however we didn't have the time to refine it to account for
questions we didn't initially consider.

This failure to adequately provide mentoring in the early stages meant that in
some cases people resorted to cargo-cult programming, and thinking that all
components had to go into this library instead of only those that would be
reused across projects, which lead to some resentment as people thought we were
enforcing requirements on them that did not exist. In retrospect education isn't
just about the hows of the system but you also need to set expectations around
its usage - often these components are suggestions for common cases and it is
fine to diverge from them and you need to clearly communicate that ideal.

We also ran into documentation issues as the time pressures from product
management meant comprehensive documentation for component usage fell by the
wayside as people became focused on building what was useful for their
individual application.

---

## Ongoing Maintenance

### <br>

Notes:

The 2013 system's small scope - focusing on a single application - meant ongoing
maintenance was straightforward. Building for a single app we could build the
component library directly within the application. Tying the system closely to
the app allowed us to rapidly develop as we were able to see changes within the
context of our app pages instead of building components isolated from where they
would be used. It was easy to add new components only when we required them and
we had the freedom to make breaking changes without worrying about other
consumers. That freedom meant we were able to avoid acruing technical debt and
the dead code of legacy components as we could tidy up all calling sites and
delete the now unused code all within a single commit.

Amen's multiple consumers lead to it being distributed as a library, which
complicated ongoing maintenance compared to the 2013 system. We now had to deal
with releasing, version numbers, managing breaking changes. Having a change to a
component be visible within the app also became more involved as you had to make
your changes in Amen, get it merged, cut a release, then update your app to the
newest version of Amen - three extra steps compared to modifying components that
directly lived within the app. We eventually got into the swing of releasing of
new versions though. We ended up having an irregular release schedule based
around when a team needed new features in Amen. An app team was free to make
changes and cut a new release at almost any time as we kept the master branch
clean and all work in progress occurred within feature branches.

This mostly worked well however sometimes we ran into issues around breaking
changes that were desired in one app but not in the other. This lead to some
duplication of components within the system - which is fine because it was the
most expedient solution to deliver value for the consuming application - but as
we didn't have the time to tidy up after those changes they often persisted for
a long time which meant the system grew to be more complex that necessary as it
contained those unremoved vestiges of legacy components.

The education shortcomings that I mentioned earlier also had an impact on
ongoing maintenance, because people were sometimes adding components to Amen
that were not suited for shared usage the library became more bloated, and the
ability to maintain that component was harmed as changes to it had to involve
two codebases instead of one.

---

## Ongoing Maintenance

### Make time for tidying

Notes:

Accruing some technical debt for the sake of delivering value and shipping
features is an acceptable trade off, however you can't keep doing it. At some
point you need to pay down that technical debt - in our case by removing unused
component variants - otherwise the system starts to crumple under its own
weight.

However as I alluded to earlier we weren't afforded the time to maintain the
health of the system after its initial creation - product management told us to
focus on delivering features within our apps and as a result this maintenance
work fell by the wayside.

If you have a dedicated component library and styleguide you need ensure you
have the time to work on paying down technical debt and to invest in features
that improve the developer experience of using the library and styleguide.

---

## Doing it all over again

Notes:

I stand by the technical decisions we made in Amen - we utilised many now-common
ideas - colocating styles and templates, using presenter classes and testing the
html output of a component all in a PHP library in 2015.

Amen's downfall can be attributed to two things: First I underestimated the
additional effort required when creating a shared system and second I assumed
product leadership would accept developers spending time to improve the
component library to allow for long term gains at the expense of short-term
feature development speed. This is not a criticism of that choice of theirs,
choosing to provide value to users is always useful but it was the mis-alignment
of their and my expectations that was the issue.

Amen overreached - we tried to do something with increased scope but we didn't
have the dedicated time to invest in the cross-team education and stewardship of
the shared components to ensure it was a success. Our vision was greater than
our ability to execute.

Amen had the goal of reducing effort through sharing code, however all that
sharing accomplished was tying together two distinct products that had slightly
different priorities, roadmaps, and work cadences. If you've ever watched a
three legged race, you'll know connecting two things that want to go in a
similar direction but at a slightly different pace doesn't really work out.

In retrospect I think we would have fared better if we said: ok we have a shared
visual language - however each team shall implement their own components that
follow that visual language, there is no need for any shared library. That way
each team would have been in full control of their own destiny and able to focus
on their own requirements rather than being tied to this shared component
library that meant they had to consider another team.

---

## TL;DR

- Match your vision to your ability to execute
- Ensure you can educate consumers
- Ensure you can own and pay down technical debt

Notes:

If you want to create a component library that is used by several teams then
you'll want it to be a project in its own right with a dedicated team to be
responsible for it. "Build it and they will come" for expansive projects doesn't
work because people need to know why and how they should use the tools you
provide and how to contribute additions. Dedicated stewardship gives the time
and space to provide that education and direction that can't happen if people
can't contribute a meaningful amount of time to the project.

At Shopify our Polaris design system has a much larger remit than these BBC
projects - we aim for it to be used by all product teams within Shopify. In
order to do that we have a dedicated team to build components, work with
consumers to educate them on how to use and contribute back to the system and to
create written documentation and examples of component usage. We have the time
and space to focus on improving Polaris's features and the developer experience
of using it and that allows it to be successful.

Our vision is big but so is our ability to live up to it, and two things being
aligned is what Amen lacked.

Creating a single shared component library is a laudable end goal but if there
isn't the time to invest in it at the moment then duplicating effort to ensure
individual teams can move at their own pace might be a better tactical choice.

---

# Thank You

### Ben Scott / <a href="http://twitter.com/BPScott">@BPScott</a>

<a href="http://www.reload.me.uk/talk-the-rise-and-fall-of-a-design-system">reload.me.uk/talk-the-rise-and-fall-of-a-design-system</a>
