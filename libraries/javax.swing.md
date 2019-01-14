# javax.swing
## Overview
javax.swing is the library built into Java for creating graphic user interfaces (GUIs). It is more challenging to use than stdlib, but significantly more powerful. For instance, in buttons, sliders, and pop-up menus.

The best way to learn Swing is probably to read chapters 10 and 11 of Horstmann's *Core Java*. The second best is to work through the code for these chapters from his website; I do this in the first couple of weeks of Software Development.

One could make a reasonable argument that there are better libraries (such as JavaFX) or more modern ways of creating GUIs (such as creating web-based interfaces). Following Hortsmann's lead, I have chosen to stick with Swing so as not to overload students with too many installations, tools, and languages.
## Additional Resources
### Online
- [*Core Java* website](http://horstmann.com/corejava/)
- [Swing API](https://docs.oracle.com/javase/8/docs/api/index.html?javax/swing/package-summary.html) (Strangely, even though Swing is included with later versions of Java, later versions of the API don't mention it.)
### Print
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Chapters 10-11
## Questions
1. :star: Which class corresponds to a visible window on the screen?
1. :star: Where is 0, 0 in the coordinate system used by Swing?
1. :star::star: If the back-end information in your program has changed and you need to re-draw something, what method should you call?
## Answers
1. [`javax.swing.JFrame`](https://docs.oracle.com/javase/8/docs/api/index.html?javax/swing/package-summary.html).
1. At the upper left. The first coordinate is the `x` coordinate from left to right (in pixels). The second is the `y` coordinate from top to bottom.
1. [`java.awt.Component.repaint`](https://docs.oracle.com/javase/8/docs/api/java/awt/Component.html#repaint--) (usually on a `JFrame`, which descends from `Component`).
