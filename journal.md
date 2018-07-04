# Journal of open-source finds and other revelations

#### Saturday, July 7, 2018

> All I want is to be someone that makes new things and thinks about them. 

— a haiku by John Maeda

__React.__ [react-beautiful-dnd](https://github.com/atlassian/react-beautiful-dnd) for drag-and-drop interactions. [What I learned from creating my first React app](https://medium.freecodecamp.org/lessons-learned-from-my-first-react-app-3c4ebb740399). [rogue](https://github.com/alidcastano/rogue) says it can do server-side rendering for React without any configuration, interesting. [react-keyboardist](https://github.com/soska/react-keyboardist) for adding keyboard shortcuts. [atomic-layout](https://github.com/kettanaito/atomic-layout) uses CSS Grid. [react-from-zero](https://github.com/kay-is/react-from-zero) is a tutorial.

__Library authoring.__ [An explanation](https://github.com/stereobooster/package.json) of all the different fields in `package.json`. [Readme Driven Development](http://tom.preston-werner.com/2010/08/23/readme-driven-development.html).

__Essays.__ [Balancing Time](https://css-tricks.com/balancing-time/) by Sarah Drasner. [Mediocre ideas, showing up, and persistence](https://chriscoyier.net/2013/10/18/mediocre-ideas-showing-up-and-persistence/) by Chris Coyier. [Reclaiming RSS](https://ar.al/2018/06/29/reclaiming-rss/).

__Accessibility.__ [Inclusive design principles](https://inclusivedesignprinciples.org/).

__Writing.__ [Tips for writing better](https://medium.com/@jesseddy/tips-for-designers-to-become-better-copywriters-from-the-experts-part-1-cbd3720cbd88).

__Infrastructure.__ [pulumi](https://www.pulumi.com/) looks great for configuring cloud infrastructure with JavaScript.

__Parting thought.__ Programming wisdom loves to diss on performance optimizations, e.g. _Rule 1: Don't do it. Rule 2 (for experts only): Don't do it yet._, root of all evil, etc. [Counterpoint](https://twitter.com/SpliterCBb/status/1011953882992431104):

> And this is why so much software runs like absolute arse.

#### Saturday, June 30, 2018

A short one this week. The case for [Headless UI Components](https://www.merrickchristensen.com/articles/headless-user-interface-components/). [This poster](https://codepen.io/adamclaxon/full/xzzxaE/) was built with CSS grid. [A refresher](https://frontendian.co/prototype) on `prototype`. [faste](https://github.com/theKashey/faste) is a state machine manager.

#### Sunday, June 24, 2018

__React.__ [react-sizeme](https://github.com/ctrlplusb/react-sizeme) sounds like it could be useful for measuring DOM nodes after they're rendered. The React folks are working on a [Profiler](https://twitter.com/brian_d_vaughn/status/1009977215176491008) tool, which may make things like _why-did-you-update_ (or my own _ytho_, which I've recently nuked), useless. [react-pdf](https://github.com/diegomura/react-pdf) promises to let you build PDFs in JSX.

__Design Systems.__ The GDS system published the [GOV.UK Design System](https://design-system.service.gov.uk/).

__Static site generators.__ [eleventy](https://github.com/11ty/eleventy) shares the ethos of marceljs. [twig.js](https://github.com/twigjs/twig.js) and [twing](https://github.com/ericmorand/twing) are two implementations of the Twig template language in JavaScript.

__Creative coding.__ [rabbitear](https://rabbitear.org/) is an origami-building library for the web.

__JavaScript.__ I didn't know this about this about the String [split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) method:

> If `separator` is a regular expression that contains capturing parentheses, then each time `separator` is matched, the results (including any undefined results) of the capturing parentheses are spliced into the output array.

__Soundtrack.__ [Driftmachine — Shunter](https://umorrex.bandcamp.com/album/shunter)

#### June 18, 2018

__React.__ [react-window](https://github.com/bvaughn/react-window) looks like a fast way to render _lots_ of objects in a viewport with React, without compromising the performance. Seems to be a refresh of [react-virtualized](https://github.com/bvaughn/react-virtualized). Speaking of refreshes, [reach-router](https://github.com/reach/router) seems like an update to [react-router](https://github.com/ReactTraining/react-router). [react-powerplug](https://github.com/renatorib/react-powerplug) has some useful little components. [react-focus-marshall](https://github.com/jossmac/react-focus-marshal) traps the keyboard tabbing focus within a component.

__Static site generators.__ [Hugo](http://gohugo.io/) is fucking fast. [Hexo](https://github.com/hexojs/hexo) is written in JavaScript and works with nunjucks templates, which are like Twig templates from PHP (or Liquid in Ruby, or Jinja2 in Python).

__Bundlers.__ [parcel](https://github.com/parcel-bundler/parcel) is fast and lovely and you set it up in about a minute for a new project. 

__Coding life.__ Finally looked at [Prettier](https://prettier.io/) and like it very much. Also added [husky](https://github.com/typicode/husky) and set up a `precommit` hook to run prettier on committed code. [docz](https://github.com/pedronauck/docz) is a promising — but still needs some work — project on writing docs for React projects using MDX (Markdown + JSX). And Facebook launched[docusaurus](https://docusaurus.io/), which is more in the vein of [Gatsby](http://gatsbyjs.org/), I think.

[create-react-library](https://github.com/transitive-bullshit/create-react-library) is something to check out soon.

__Soundtrack.__ Roger Eno — Dust of Stars
