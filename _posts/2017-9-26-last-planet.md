---
layout: post
title: "Last Planet"
description: "2D Metroidvania like game, support both Windows and MacOS."
tags: [opengl, directx, cpp, mac, windows]
---

An Metroidvania game I created for both Windows and MacOS. Feel free to download and play. :earth_asia:

<div class="embed-responsive embed-responsive-16by9">
<iframe src="https://www.youtube.com/embed/qx6eEB96-N0?loop=1&playlist=qx6eEB96-N0&modestbranding=1&autohide=1&showinfo=0&controls=0" allowfullscreen></iframe>
</div>

## Features

MacOS and Windows version have some different features:

- `open world` a real open world platform game.
- `physics & collision` automatically check for all possible collision.
- `level design` all levels design by myself, totally 24 areas, with check point.
- `kinds of enemies` different kinds of enemies and behavior, one last boss.
- `items` several hidden items that can level up player's abilities.
- `particles system` a particle system for bullet and explosion.
- `uv animation` shader based uv animation and effect.
- `game object` game object based coding like Unity.
- `music and sound` background music and sound effect perfectly fit for every situations.
- `full game experience` from title to game over, check point, death punishment, etc.
- `tile map editor` support tile map editor.
- `hard` very hard, but there always a simple way to clear.

## Download

- `OSX` [download](https://drive.google.com/file/d/1BoMI938O3L1ZRnvUED7IXxvYIc6osHxn/view?usp=sharing){:target="blank"} :sparkles:  (OSX 10.13 or later). Check source code [here](https://github.com/haijianliu/vania-opengl-cpp){:target="blank"}.
- `Win` [download](https://drive.google.com/file/d/1quQ_V_do9t3M2WUbaYGuB0SdyehrlhnP/view?usp=sharing){:target="blank"}.

{% include image.html path="2017-9-26-last-planet/last_planet@2x.png" path-detail="2017-9-26-last-planet/last_planet_full@2x.png" alt="last planet" %}

## Tiled Map Editor

All levels were created with Tiled Map Editor by [Thorbjørn](https://thorbjorn.itch.io){:target="blank"}, including enemies, items, checkpoints, colliders, camera behavior, event triggers.

{% include image.html path="2017-9-26-last-planet/tiled_map_editor@2x.png" path-detail="2017-9-26-last-planet/tiled_map_editor_full@2x.png" alt="tiled map editor" %}

## Frameworks

- `OpenGL ES 3.2 & GLM` Core graphic api and core math library for OSX.
- `stb` Public domain C image loading library by [nothings](http://nothings.org){:target="blank"}.
- `irrKlang` Cross platform sound library for C++, C# and all .NET languages by [Ambiera](https://www.ambiera.com/irrklang/){:target="blank"}.
- `DirectX 9` For Windows.

## Credits

- Design and Code by [Haijian Liu](https://haijianliu.github.io){:target="blank"}.
- Character and Animation by [Luis Zuno](http://ansimuz.com){:target="blank"}.
- BGM by SketchyLogic from [OpenGameArt](https://opengameart.org){:target="blank"}.
- SE by Juhani Junkala from [OpenGameArt](https://opengameart.org){:target="blank"}.
