---
title: "Work"
layout: tiled-wall
---

Plein air paintings and urban sketches\
from Scotland and around the world.
{:.lead}


Favourite subjects

<main class="blog-posts">
  
  <div class="post-tiles-masonry" id="postcards">
    {%- for page in site.work limit: 9 %}
      <div class="post-tiles-masonry-item" data-category="{{ page.categories | join: ';' }}" {% if page.img %}data-img="{{ page.img | img_url_prefix }}"{% endif %}>
        <a href="{{ page.url | relative_url }}">
          {%- if page.coverimg -%}
            <img src="{{ site.imgsrc }}/{{ page.coverimg }}" />
          {%- endif -%}
          <span class="post-title">
            {{ page.title }}
          </span>
        </a>
      </div>
    {%- endfor %}
  </div>
</main>

<script>
  // display tiles only once all images loaded
  Promise.all(Array.from(document.querySelectorAll(".post-tiles-masonry-item a img")).filter(img => !img.complete).map(img => new Promise(resolve => { img.onload = img.onerror = resolve; }))).then(() => {
    var masonry = new MiniMasonry({
        container: '.post-tiles-masonry',
        baseWidth: 240,
        gutterX: 40,
        gutterY: 60,
        surroundingGutter: false
    });
    document.getElementById("postcards").setAttribute("style", "opacity:1");
  });
</script>