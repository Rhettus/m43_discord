---
layout: default
title: Guides & Resources
---

# M43 Guides & Resources

Learn everything you need to know about the Micro Four Thirds system, from buying your first camera to advanced techniques.

## All Guides

<div class="card-grid">
{% for guide in site.guides %}
  <div class="card">
    <h3><a href="{{ guide.url | relative_url }}">{{ guide.title }}</a></h3>
    
    {% if guide.excerpt %}
    <p>{{ guide.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
    
    {% if guide.tags %}
    <div style="margin-top: 1rem;">
      {% for tag in guide.tags %}
      <span class="card-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
    
    <div style="margin-top: 1rem;">
      <a href="{{ guide.url | relative_url }}" class="btn">Read Guide</a>
    </div>
  </div>
{% endfor %}
</div>

{% if site.guides.size == 0 %}
<div style="text-align: center; padding: 3rem; background: white; border-radius: 8px; margin-top: 2rem;">
  <p style="font-size: 1.2rem; color: #666;">Guides coming soon! Check back later.</p>
</div>
{% endif %}

## Quick Reference

### Popular Camera Bodies

- **Olympus OM-D E-M1 Mark III** - Pro flagship with excellent IBIS
- **Panasonic GH6** - Video powerhouse
- **OM System OM-1** - Latest flagship with stacked sensor
- **Panasonic G9** - High-speed stills camera
- **Olympus E-M5 Mark III** - Compact enthusiast option

### Lens Recommendations by Use Case

**Street Photography:** 17mm f/1.8, 25mm f/1.8, 45mm f/1.8
**Landscape:** 7-14mm f/2.8, 12-40mm f/2.8
**Portrait:** 25mm f/1.2, 45mm f/1.2, 75mm f/1.8
**Wildlife:** 40-150mm f/2.8, 100-400mm f/5-6.3
**Travel:** 12-40mm f/2.8, 12-100mm f/4

### Essential Accessories

- Extra batteries (BLX-1, BLH-1, or DMW-BLF19)
- Fast SD cards (V30 or higher for video)
- Lens filters (UV, CPL, ND)
- Camera strap or Peak Design system
- Lens cleaning kit

## Contributing

Have expertise to share? Want to write a guide? Join our Discord community and help other M43 users!