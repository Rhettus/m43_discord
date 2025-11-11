---
layout: default
title: Home
---

# Welcome to the M43 Reference Hub

Your community-curated guide to the Micro Four Thirds system. Find lens recommendations, YouTube channels, buying guides, and everything you need to make the most of your M43 gear.

## Quick Links

<div class="card-grid">
  <div class="card">
    <h3>📷 Lens Database</h3>
    <p>Browse our comprehensive collection of M43 lenses with specs, reviews, and sample images.</p>
    <a href="{{ '/lenses' | relative_url }}" class="btn">View Lenses</a>
  </div>
  
  <div class="card">
    <h3>🎥 YouTube Channels</h3>
    <p>Discover the best M43 content creators, reviewers, and tutorial channels.</p>
    <a href="{{ '/channels' | relative_url }}" class="btn">Explore Channels</a>
  </div>
  
  <div class="card">
    <h3>📚 Guides & Resources</h3>
    <p>Learn about camera bodies, firmware updates, accessories, and shooting techniques.</p>
    <a href="{{ '/guides' | relative_url }}" class="btn">Read Guides</a>
  </div>
</div>

## Latest Additions

{% for lens in site.lenses limit:3 %}
- **{{ lens.title }}** - {{ lens.manufacturer }} | {{ lens.focal_length }} | {{ lens.aperture }}
{% endfor %}

## Why Micro Four Thirds?

Micro Four Thirds offers the perfect balance of image quality, portability, and affordability. With a huge selection of lenses, excellent stabilization, and a passionate community, M43 is ideal for everyone from beginners to professionals.

---

*This site is maintained by the M43 Discord community. Want to contribute? Join us on Discord!*