# cayleyGraphVisualizer

Created with CodeSandbox

8/8/25-8/9/25 experiment

Written completely by ChatGPT, under my guidance/prompting. It works shockingly well.

View it at this link [https://codesandbox.io/p/github/danirui/cayleyGraphVisualizer/main](https://codesandbox.io/p/github/danirui/cayleyGraphVisualizer/main). On the right hand side panel, click `Start 3000` and the Preview should open. (May need to do Project Setup, click all the way through, and at the end do Preview3000?)

As usual, click and drag on the viewing window to rotate (around a fixed origin), scroll to zoom in and out, and right-click and drag to translate the things on screen around (the origin of rotation seems to remain fixed).

---

## Slightly more technical user manual

Nodes will have labels (may have to wait a bit before they load/appear in the correct places), unless you don't want them in which case you can hide them by toggling a button in the control panel.

The UI is intuitive, self-explanatory. The "physics" engine (jostling, repulsion, springs, etc.) is to evolve the Cayley graph into a nice geometric shape.

Different colored edges now can have different spring tensions. Also, users can now hover over (more info appears) and click nodes (color changes to yellow) to (1.) pin in place and (2.) drag nodes to different places manually, in case the stochastic jostling is not producing desirable results.

Small quirk: once you click a node once, the scroll/pan/rotate/zoom capabilities shut off (a side-effect of trying to make it so that dragging a node around doesn't also rotate/pan/scroll the viewing window). But if you click multiple nodes (turning them all yellow --- you may have to lightly drag/throw a node before you click it), and you "unclick" just one of them (also by lightly dragging/throwing it), the scroll/pan/rotate/zoom capabilities come back.

Another small quirk: `springK` also controls the "natural length" of a spring; the higher the value, the shorter the natural length, so the visual effect is that setting `springK` high means all the edges _want_ to contract.

---

A sample of some things I asked ChatGPT (at the very beginning; the later minor tweaks took a lot more back-and-forth):

> in this video [https://www.youtube.com/watch?app=desktop&v=HbEd3Sef13I&ab_channel=WhatisMath%3F](https://www.youtube.com/watch?app=desktop&v=HbEd3Sef13I&ab_channel=WhatisMath%3F) some cayley graphs are depicted. in particular the group G = S_4 and set of generators S = (12), (13), (34)
> and G = A_5 and set of generators S = (12)(34), (12345), (54321)
>
> I want to write code visualizing cayley graphs of groups, as follows: user interface should begin with G=S_n. User gets to choose set of generators S (maybe some presets or a list of recommendations)
>
> Then one can generate the cayley graph abstractly (some work needs to be done to see if 2 "words" refer to the same element, you'll have to figure it out).

> just print out all the nodes: starting node is e (permutation \[1234\]), then say apply R=Red=(12) to get to \[2134\]. so the printed list should look something like
>
> \[1234\]: e
>
> \[2134\]: R
>
> \[2143\]: YR "apply red, then yellow, reading right to left"
>
> etc.

> The next step is to visualize it. One idea is to plot in 3d, and have springs on the edges with strengths that the user can manipulate on a slide perhaps, + jostling whose strength the user can also manipulate, that will stretch and pull the abstract graph into a stable 3D configuration. this should play as a live animation, where again the user can change things on slides for example and see it reflected in the animation.

> it may help to look over this website [https://juliapoo.github.io/mathematics/2023/07/15/plotting-cayley-graphs.html](https://juliapoo.github.io/mathematics/2023/07/15/plotting-cayley-graphs.html) and its source code [https://github.com/JuliaPoo/Cayley-Graph-Plotting](https://github.com/JuliaPoo/Cayley-Graph-Plotting) for inspiration. in particular, nice features are arrows on the edges, labels on edge corresponding to an element of S, Julia's smooth animations. dragging around mouse rotates, scrolling zooms
