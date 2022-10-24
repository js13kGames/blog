---
title:   What’s new in Kontra.js v7
date:    2020-08-28
authors:
	- @straker
tags:
	- Guest Post
	- Kontra.js
	- TypeScript
	- Sprites
	- MadMarcel
	- Mega Man
	- Vector
	- Text
	- Buttons
	- Scenes
	- Grid
	- ES Module Imports
	- Rollup
	- Webpack
	- Plugin
summary: Kontra.js v7 was released a few weeks ago. With it brings a host of new functionality and components as well as a new way to reduce the overall file size.
---

Kontra.js v7 was released a few weeks ago. With it brings a host of new functionality and components as well as a new way to reduce the overall file size.

For a complete list of changes, see the [v7 release notes](//github.com/straker/kontra/releases/tag/v7.0.0).

## TypeScript support

One of the new features this release is TypeScript support. I was surprised last year by how many users wanted to use Kontra.js with TypeScript so I made sure to include support for it.

## New functionality

The Sprite component got a few new features this version. The biggest one is group support, allowing you to add children to other Sprites and have them update and render as a single unit. [@madmarcel](http://twitter.com/madmarcel) already [took it for a test drive](//twitter.com/madmarcel/status/1293533757035560960) and built a sweet scene of a Mega Man style dragon boss where each body part was its own sprite with a single parent.

![Mega Man style animated dragon boss](dragon-boss.gif)

Other new Sprite features include opacity and scaling of objects.

The Vector component also got a bunch of new functions dedicated to vector math: angle, distance, dot, length, normalize, scale, and subtract.

Lastly, v7 ships with a new group of [helper functions](//straker.github.io/kontra/api/helpers) to help with common gamedev needs. Functions include converting between degrees and radians, getting a random integer, and a seeded random number generator.

## New components

The new version introduces four new components to the library that are focused on UI elements: Text, Buttons, Scenes, and Grid.

The [Text component](//straker.github.io/kontra/api/text) makes it simple to draw text to the screen and supports multiline text and RTL languages.

The [Button component](//straker.github.io/kontra/api/button) helps you create an interactive button that work with mouse, touch, or keyboard events. The Button is also accessible and supports screen readers out of the box. With Text and Buttons creating menus and UI should be a lot easier.

The [Scene component](//straker.github.io/kontra/api/scene) was a highly requested feature and enables organizing a group of objects that will update and render together.

Lastly, and my personal favorite feature, the [Grid component](//straker.github.io/kontra/api/grid) makes creating menus super easy. One of the things I despised about creating menus was having to hand place every button and figuring out how to manage updating all that if the UI scale / font size increased. The Grid component automatically handles all that for you which makes creating menus a breeze.

## Further size reduction

Last year I [put together a poll](//twitter.com/StevenKLambert/status/1172875307767889927) of what users wanted out of the library and the number one thing was smaller file size. It was very common for users to remove entire parts of the Sprite component in order to reduce the file size.

Even though the library is written using ES Module Imports, module bundlers such as Rollup or Webpack cannot remove any of the unused functionality of a component. So even if all you wanted from the Sprite component was the ability to draw a rectangle, you would get all the rest of the functionality along with it, bloating the file size.

To support more granular control over the file size, I created [rollup-plugin-kontra](//github.com/straker/rollup-plugin-kontra) which allows you to specify which functionality you need and it will safely remove the rest. This should allow you to get the absolute smallest file size possible out of the library.