---
layout: post
title: "Motion and Lighting"
description: "Bone animation and PBR lighting test scene."
tags: [opengl, cpp, mac]
---

Animations: idle, run, attack. 4 point PBR lights in different colors. Maybe a little dark. :first_quarter_moon_with_face:

<div class="embed-responsive embed-responsive-16by9">
<iframe src="https://www.youtube.com/embed/Jx8-Af0wazw?loop=1&playlist=Jx8-Af0wazw&modestbranding=1&autohide=1&showinfo=0&controls=0" allowfullscreen></iframe>
</div>

## Features

Features currently supported:

- `PBR` real time physics base rendering algorithm and HDR.
- `render pass` separated render pass: G-buffer, lighting, shadow mapping, SSAO.
- `shadow mapping` real time shader based shadow mapping.
- `SSAO` real time screen-space SSAO.
- `ECS` Entity Component & GameObject System just like Unity Engine.
- `motion blending` bone animation blending, supporting all the animations from mixamo.com.
- `third person controller` player-camera controller just like all the third person game, supporting PS4 controller.

## Frameworks

- `OpenGL ES 3.2 & GLM` Core graphic api and core math library.

- `Assimp` Although I have wrote some model loader program by myself, Assimp is more professional library and can handle more complex situations. [Open Asset Import Library (short name: Assimp)](http://assimp.sourceforge.net){:target="blank"} is a portable Open Source library to import various well-known 3D model formats in a uniform manner.

- `stb` Public domain C image loading library by [nothings](http://nothings.org){:target="blank"}.

## Assets

- Character and animation from [mixamo](https://www.mixamo.com){:target="blank"}.

## Bibliography
- [Background: Physics and Math of Shading by Naty Hoffmann](http://blog.selfshadow.com/publications/s2013-shading-course/hoffman/s2013_pbs_physics_math_notes.pdf){:target="blank"}.
- [Real shading in Unreal Engine 4](http://blog.selfshadow.com/publications/s2013-shading-course/karis/s2013_pbs_epic_notes_v2.pdf){:target="blank"}.
- [Unity User Manual](https://docs.unity3d.com/Manual/index.html){:target="blank"}.
- [Learn OpenGL, extensive tutorial resource for learning Modern OpenGL](https://learnopengl.com){:target="blank"}.
