---
layout: post
title: "Frustum culling"
description: "View frustum culling feature show case."
tags: [opengl, cpp, mac]
---

The goal of view frustum culling is to be able to identify what is inside the frustum (totally or partially), and cull everything that is not inside. Only the stuff that is inside the frustum, even if only partially, is sent to the graphics hardware. This Process is not only working with meshes, but also wording with particles and lights.

{% include image.html path="2017-11-25-frustum-culling/frustum_culling_screen@2x.png" path-detail="2017-11-25-frustum-culling/frustum_culling_screen_full@2x.png" alt="frustum culling" %}

## Bounding box

A bounding box will be generated during the loading process for each GameObject.
{% include image.html path="2017-11-25-frustum-culling/bounding_box_screen@2x.png" path-detail="2017-11-25-frustum-culling/bounding_box_screen_full@2x" alt="bounding box" %}

Obtain a light's volume radius by solving the attenuation equation. However, this equation will never exactly reach the value zero, so there won't be a solution. But solve it for a brightness value that is close to zero.

{% highlight cpp %}
float lightMax = glm::max(glm::max(this->color.x, this->color.y), this->color.z) * this->intensity;
this->radius = 8 * glm::sqrt(lightMax / 5);
{% endhighlight %}

## Test demo

The frustum process will never be seen by player, however I created a test camera which can switch between default perspective and test perspective.
<div class="embed-responsive embed-responsive-16by9">
<iframe src="https://www.youtube.com/embed/fZONvOo_tD4?loop=1&playlist=fZONvOo_tD4&modestbranding=1&autohide=1&showinfo=0&controls=0" allowfullscreen></iframe>
</div>

## Implementation
Frustum culling process is only happening with the main camera. So I make it a component, which only need to be attached to camera object.
{% highlight cpp %}
GameObject* camera = new GameObject();
camera->addComponent<Camera>();
camera->addComponent<Transform>();
camera->addComponent<FrustumCulling>();
scene->mainCamera = camera;
scene->addGameObject("mainCamera", camera);
{% endhighlight %}
