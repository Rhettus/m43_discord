---
layout: default
title: M43 Lenses
---

# Micro Four Thirds Lens Database

Browse our comprehensive collection of M43 lenses from all major manufacturers. Find the perfect lens for your photography style.

## Filter by Type

<div class="filter-tags">
  <button class="filter-btn active" data-filter="all">All Lenses</button>
  <button class="filter-btn" data-filter="prime">Prime</button>
  <button class="filter-btn" data-filter="zoom">Zoom</button>
</div>

## All Lenses

<div class="card-grid">
{% for lens in site.lenses %}
  <div class="card lens-card" data-type="{{ lens.type | downcase }}">
    <h3><a href="{{ lens.url | relative_url }}">{{ lens.title }}</a></h3>
    
    <div class="lens-quick-specs">
      {% if lens.manufacturer %}
      <div><strong>Brand:</strong> {{ lens.manufacturer }}</div>
      {% endif %}
      {% if lens.focal_length %}
      <div><strong>Focal Length:</strong> {{ lens.focal_length }}</div>
      {% endif %}
      {% if lens.aperture %}
      <div><strong>Aperture:</strong> {{ lens.aperture }}</div>
      {% endif %}
      {% if lens.type %}
      <div><strong>Type:</strong> {{ lens.type }}</div>
      {% endif %}
    </div>
    
    {% if lens.rating %}
    <div class="lens-rating">
      ⭐ {{ lens.rating }}/5
    </div>
    {% endif %}
    
    {% if lens.tags %}
    <div style="margin-top: 1rem;">
      {% for tag in lens.tags %}
      <span class="card-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
    
    <div style="margin-top: 1rem;">
      <a href="{{ lens.url | relative_url }}" class="btn">View Details</a>
    </div>
  </div>
{% endfor %}
</div>

{% if site.lenses.size == 0 %}
<div style="text-align: center; padding: 3rem; background: white; border-radius: 8px;">
  <p style="font-size: 1.2rem; color: #666;">No lenses added yet. Check back soon!</p>
</div>
{% endif %}

## Contribute

Know a lens that should be on this list? Have sample images or a detailed review to share? Join our Discord and help us build the most comprehensive M43 lens database!

<style>
.filter-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin: 2rem 0;
  padding: 1.5rem;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.filter-btn {
  padding: 0.5rem 1rem;
  border: 2px solid var(--border);
  background: white;
  border-radius: 20px;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.3s;
}

.filter-btn:hover {
  border-color: var(--secondary);
  background: var(--secondary);
  color: white;
}

.filter-btn.active {
  background: var(--primary);
  border-color: var(--primary);
  color: white;
}

.lens-quick-specs {
  margin: 1rem 0;
  padding: 1rem;
  background: var(--light);
  border-radius: 6px;
  font-size: 0.9rem;
}

.lens-quick-specs div {
  margin: 0.5rem 0;
}

.lens-rating {
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--accent);
  margin: 0.5rem 0;
}
</style>

<script>
// Filter functionality
document.querySelectorAll('.filter-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    this.classList.add('active');
    
    const filter = this.dataset.filter.toLowerCase();
    document.querySelectorAll('.lens-card').forEach(card => {
      if (filter === 'all') {
        card.style.display = 'block';
      } else {
        const cardType = card.dataset.type ? card.dataset.type.toLowerCase() : '';
        // Check if filter matches type or is contained in type
        if (cardType === filter || cardType.includes(filter)) {
          card.style.display = 'block';
        } else {
          card.style.display = 'none';
        }
      }
    });
  });
});
</script>