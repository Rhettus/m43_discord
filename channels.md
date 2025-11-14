---
layout: default
title: YouTube Channels
---

# M43 YouTube Channels

Discover the best YouTube channels for Micro Four Thirds content, from gear reviews to shooting tutorials and creative inspiration.

## Filter by Category

<div class="filter-tags">
  <button class="filter-btn active" data-filter="all">All Channels</button>
  <button class="filter-btn" data-filter="reviews">Reviews</button>
  <button class="filter-btn" data-filter="tutorials">Tutorials</button>
  <button class="filter-btn" data-filter="vlogs">Vlogs</button>
  <button class="filter-btn" data-filter="wildlife">Wildlife</button>
  <button class="filter-btn" data-filter="street">Street</button>
</div>

<div class="card-grid">
{% for channel in site.channels %}
  <div class="card">
    <div class="card-header-with-image">
      {% if channel.image %}
      <img src="{{ channel.image | relative_url }}" alt="{{ channel.title }}" class="channel-avatar">
      {% else %}
      <div class="channel-avatar-placeholder">{{ channel.title | slice: 0 }}</div>
      {% endif %}
      <div class="card-header-text">
        <h3><a href="{{ channel.url | relative_url }}">{{ channel.title }}</a></h3>
        <div class="card-meta">
          {% if channel.subscribers %}
          <span>👥 {{ channel.subscribers }}</span>
          {% endif %}
          {% if channel.upload_frequency %}
          <span>• {{ channel.upload_frequency }}</span>
          {% endif %}
        </div>
      </div>
    </div>
    
    {% if channel.tags %}
    <div style="margin-top: 1rem;">
      {% for tag in channel.tags %}
      <span class="card-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
    
    <div style="margin-top: 1rem;">
      <a href="{{ channel.url | relative_url }}" class="btn">View Details</a>
      {% if channel.channel_url %}
      <a href="{{ channel.channel_url }}" target="_blank" style="margin-left: 0.5rem; color: var(--accent);">Visit Channel →</a>
      {% endif %}
    </div>
  </div>
{% endfor %}
</div>

## Can't Find What You're Looking For?

Know a great M43 YouTube channel that's not listed? Join our Discord and let us know! We're always looking to expand our community resources.

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

.card-header-with-image {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 1rem;
}

.channel-avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  flex-shrink: 0;
  border: 2px solid var(--border);
}

.channel-avatar-placeholder {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: var(--primary);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: 700;
  flex-shrink: 0;
}

.card-header-text {
  flex: 1;
  min-width: 0;
}

.card-header-text h3 {
  margin-bottom: 0.25rem;
}

.card-meta {
  font-size: 0.9rem;
  color: #666;
}
</style>

<script>
// Simple filter functionality (optional - can be enhanced)
document.querySelectorAll('.filter-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    this.classList.add('active');
    
    const filter = this.dataset.filter;
    document.querySelectorAll('.card').forEach(card => {
      if (filter === 'all') {
        card.style.display = 'block';
      } else {
        const tags = card.querySelector('.card-tag');
        if (tags && tags.textContent.toLowerCase().includes(filter)) {
          card.style.display = 'block';
        } else {
          card.style.display = 'none';
        }
      }
    });
  });
});
</script>