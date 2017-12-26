---
layout: post
title: "Lookup table post processing effect"
description: "Use lookup table textures to apply color transforms in a shader."
tags: [opengl, cpp, mac]
---

I have been working on a personal rendering engine these days. Find the previous tease [here](https://haijianliu.github.io/posts/dungeon-demo). This demo is for LUT post processing effect test.
Here I used some lookup tables from Unreal Engine to apply color transforms in a shader.

{% include image.html path="2017-12-26-lut-post-effect/lut_half@2x.png" path-detail="2017-12-26-lut-post-effect/lut_half_full@2x.png" alt="clut preview" %}

## Spec

3D textures are used, and the size of lookup table is (16x16)x16.

{% include image.html path="2017-12-26-lut-post-effect/clut_default_rgb.png" path-detail="2017-12-26-lut-post-effect/clut_default_rgb.png" alt="clut default rgb" %}

channels:

{% include image.html path="2017-12-26-lut-post-effect/clut_default_r.png" path-detail="2017-12-26-lut-post-effect/clut_default_r.png" alt="clut default r" %}

{% include image.html path="2017-12-26-lut-post-effect/clut_default_g.png" path-detail="2017-12-26-lut-post-effect/clut_default_g.png" alt="clut default g" %}

{% include image.html path="2017-12-26-lut-post-effect/clut_default_b.png" path-detail="2017-12-26-lut-post-effect/clut_default_b.png" alt="clut default b" %}


## Shader

Apply the lookup table after the final combination of all the other passes. Since the output value of 'combine pass' is followed by an tone mapping processing, none of the RGB values will reach 1.0. And it is better to use some precomputed numbers. (etc. 0.03125 is 1/32)

{% highlight glsl %}
out vec4 lutPass;

in vec2 uv;

uniform sampler2D combinePass;
uniform sampler2D lut;

void main() {
	vec3 combineColor = texture(combinePass, uv).rgb;

	float blueIndex = floor(combineColor.b * 16.0); // 0 ~ 15

	vec2 uvMapping;
	uvMapping.x = (blueIndex + 0.03125 + 0.9375 * combineColor.r) * 0.0625;
	uvMapping.y = 0.03125 + 0.9375 * combineColor.g;

	lutPass = vec4(texture(lut, uvMapping).rgb, 1);
}
{% endhighlight %}

And mipmap mode needed to be disabled for a lookup table image. Use `GL_LINEAR` for a better looking.

{% highlight c %}
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_EDGE);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_EDGE);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
{% endhighlight %}

## Demo

For test, Here is a `LutController` Component attached to `gameControl` GameObject, which can switch lookup tables by pushing left or right key.

<div class="embed-responsive embed-responsive-16by9">
<iframe src="https://www.youtube.com/embed/uIYNtmrwrsA?loop=1&playlist=uIYNtmrwrsA&modestbranding=1&autohide=1&showinfo=0&controls=0" allowfullscreen></iframe>
</div>


## Assets

- Character and animation from [mixamo](https://www.mixamo.com){:target="blank"}.
- Model by SilverTm from [UE4 Marketplace](https://www.unrealengine.com/marketplace){:target="blank"}.

## Bibliography
- [Lookup table - Wikipedia](https://en.wikipedia.org/wiki/Lookup_table){:target="blank"}.
- [Lookup table color transforms for glslify by mattdesl](https://github.com/mattdesl/glsl-lut){:target="blank"}.
