---
layout: default
title: Member Portfolios
---

# M43 Community Member Portfolios

Discover the amazing work of our community members! Browse portfolios from photographers around the world shooting with Micro Four Thirds.

## Filter by Style

<div class="filter-tags">
  <button class="filter-btn active" data-filter="all">All Members</button>
  <button class="filter-btn" data-filter="wildlife">Wildlife</button>
  <button class="filter-btn" data-filter="landscape">Landscape</button>
  <button class="filter-btn" data-filter="street">Street</button>
  <button class="filter-btn" data-filter="portrait">Portrait</button>
  <button class="filter-btn" data-filter="macro">Macro</button>
  <button class="filter-btn" data-filter="birds">Birds</button>
</div>

## Community Photographers

<div class="card-grid">
{% for member in site.portfolios %}
  <div class="card portfolio-card" data-tags="{{ member.tags | join: ',' | downcase }}">
    <div class="card-header-with-image">
      {% if member.image %}
      <img src="{{ member.image | relative_url }}" alt="{{ member.name }}" class="portfolio-avatar">
      {% else %}
      <div class="portfolio-avatar-placeholder">{{ member.name | slice: 0 }}</div>
      {% endif %}
      <div class="card-header-text">
        <h3>{{ member.name }}</h3>
        {% if member.location %}
        <div class="portfolio-location">📍 {{ member.location }}</div>
        {% endif %}
      </div>
    </div>
    
    {% if member.bio %}
    <p class="portfolio-bio">{{ member.bio }}</p>
    {% endif %}
    
    {% if member.tags %}
    <div class="portfolio-tags">
      {% for tag in member.tags %}
      <span class="card-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
    
    {% if member.website or member.instagram or member.flickr or member.twitter or member.youtube or member.facebook %}
    <div class="portfolio-links">
      {% if member.website %}
      <a href="{{ member.website }}" target="_blank" rel="noopener noreferrer" title="Website">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><line x1="2" y1="12" x2="22" y2="12"></line><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"></path></svg>
      </a>
      {% endif %}
      {% if member.instagram %}
      <a href="{{ member.instagram }}" target="_blank" rel="noopener noreferrer" title="Instagram">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
      </a>
      {% endif %}
      {% if member.flickr %}
      <a href="{{ member.flickr }}" target="_blank" rel="noopener noreferrer" title="Flickr">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><circle cx="6.5" cy="12" r="4.5"></circle><circle cx="17.5" cy="12" r="4.5"></circle></svg>
      </a>
      {% endif %}
      {% if member.twitter %}
      <a href="{{ member.twitter }}" target="_blank" rel="noopener noreferrer" title="Twitter/X">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4l11.733 16h4.267l-11.733 -16z"></path><path d="M4 20l6.768 -6.768m2.46 -2.46l6.772 -6.772"></path></svg>
      </a>
      {% endif %}
      {% if member.youtube %}
      <a href="{{ member.youtube }}" target="_blank" rel="noopener noreferrer" title="YouTube">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22.54 6.42a2.78 2.78 0 0 0-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 0 0-1.94 2A29 29 0 0 0 1 11.75a29 29 0 0 0 .46 5.33A2.78 2.78 0 0 0 3.4 19c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 0 0 1.94-2 29 29 0 0 0 .46-5.25 29 29 0 0 0-.46-5.33z"></path><polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02"></polygon></svg>
      </a>
      {% endif %}
      {% if member.facebook %}
      <a href="{{ member.facebook }}" target="_blank" rel="noopener noreferrer" title="Facebook">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path></svg>
      </a>
      {% endif %}
    </div>
    {% endif %}
  </div>
{% endfor %}
</div>

{% if site.portfolios.size == 0 %}
<div style="text-align: center; padding: 3rem; background: white; border-radius: 8px; margin-top: 2rem;">
  <p style="font-size: 1.2rem; color: #666;">No member portfolios yet. Want to be featured? Join our Discord!</p>
</div>
{% endif %}

## Want to Be Featured?

If you're an M43 photographer and want to showcase your work here, join our Discord server and share your portfolio!

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

.portfolio-avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  flex-shrink: 0;
  border: 2px solid var(--border);
}

.portfolio-avatar-placeholder {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: var(--accent);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: 700;
  flex-shrink: 0;
}

.portfolio-location {
  font-size: 0.9rem;
  color: #666;
  margin-top: 0.25rem;
}

.portfolio-bio {
  font-size: 0.95rem;
  color: #555;
  line-height: 1.5;
  margin: 1rem 0;
}

.portfolio-tags {
  margin: 1rem 0;
}

.portfolio-links {
  display: flex;
  gap: 1rem;
  margin-top: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid var(--border);
}

.portfolio-links a {
  color: var(--primary);
  transition: color 0.3s, transform 0.2s;
  display: flex;
  align-items: center;
}

.portfolio-links a:hover {
  color: var(--accent);
  transform: translateY(-2px);
}

.portfolio-links svg {
  width: 24px;
  height: 24px;
}
</style>

<script>
// Filter functionality
document.querySelectorAll('.filter-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    this.classList.add('active');
    
    const filter = this.dataset.filter.toLowerCase();
    document.querySelectorAll('.portfolio-card').forEach(card => {
      if (filter === 'all') {
        card.style.display = 'block';
      } else {
        const cardTags = card.dataset.tags ? card.dataset.tags.toLowerCase() : '';
        card.style.display = cardTags.includes(filter) ? 'block' : 'none';
      }
    });
  });
});
</script>