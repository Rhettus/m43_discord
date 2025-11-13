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
  <button class="filter-btn" data-filter="weathersealed-yes">Weather Sealed</button>
  <button class="filter-btn" data-filter="weathersealed-no">Not Weather Sealed</button>
  <button class="filter-btn" data-filter="autofocus-yes">Autofocus</button>
  <button class="filter-btn" data-filter="autofocus-no">Manual Focus</button>
</div>

## All Lenses

<div class="lens-table-container">
  <table id="lensTable" class="lens-table">
    <thead>
      <tr>
        <th data-sort="title">Lens Name <span class="sort-arrow">↕</span></th>
        <th data-sort="focal_length">Focal Length <span class="sort-arrow">↕</span></th>
        <th data-sort="aperture">Max Aperture <span class="sort-arrow">↕</span></th>
        <th data-sort="type">Type <span class="sort-arrow">↕</span></th>
        <th data-sort="weight">Weight <span class="sort-arrow">↕</span></th>
        <th data-sort="price_range">Price <span class="sort-arrow">↕</span></th>
        <th data-sort="magnification">Magnification <span class="sort-arrow">↕</span></th>
        <th data-sort="autofocus">Auto Focus <span class="sort-arrow">↕</span></th>
        <th data-sort="weathersealed">Weather Sealed <span class="sort-arrow">↕</span></th>
      </tr>
    </thead>
    <tbody>
{% for lens in site.lenses %}
      <tr class="lens-row" data-type="{{ lens.type | downcase }}" data-weathersealed="{% if lens.weathersealed == true or lens.weathersealed == 'Yes' %}yes{% else %}no{% endif %}" data-autofocus="{% if lens.autofocus == true or lens.autofocus == 'Yes' %}yes{% else %}no{% endif %}">
        <td class="lens-name"><a href="{{ lens.url | relative_url }}">{{ lens.title }}</a></td>
        <td data-value="{{ lens.focal_length }}">{{ lens.focal_length | default: "—" }}</td>
        <td data-value="{{ lens.aperture }}">{{ lens.aperture | default: "—" }}</td>
        <td>{{ lens.type | default: "—" }}</td>
        <td data-value="{{ lens.weight }}">{{ lens.weight | default: "—" }}</td>
        <td>{{ lens.price_range | default: "—" }}</td>
        <td>{{ lens.magnification | default: "—" }}</td>
        <td>{% if lens.autofocus == true or lens.autofocus == "Yes" %}Yes{% elsif lens.autofocus == false or lens.autofocus == "No" %}No{% else %}{{ lens.autofocus | default: "Yes" }}{% endif %}</td>
        <td>{% if lens.weathersealed == true or lens.weathersealed == "Yes" %}Yes{% elsif lens.weathersealed == false or lens.weathersealed == "No" %}No{% else %}{{ lens.weathersealed | default: "No" }}{% endif %}</td>
      </tr>
{% endfor %}
    </tbody>
  </table>
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

.lens-table-container {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  overflow-x: auto;
  margin: 2rem 0;
}

.lens-table {
  width: 100%;
  border-collapse: collapse;
  margin: 0;
}

.lens-table thead {
  background: var(--primary);
  color: white;
  position: sticky;
  top: 0;
  z-index: 10;
}

.lens-table th {
  padding: 1rem;
  text-align: left;
  font-weight: 600;
  cursor: pointer;
  user-select: none;
  white-space: nowrap;
  border-bottom: none;
}

.lens-table th:hover {
  background: var(--secondary);
}

.sort-arrow {
  font-size: 0.8em;
  margin-left: 0.25rem;
  opacity: 0.5;
}

.lens-table th.sort-asc .sort-arrow {
  opacity: 1;
}

.lens-table th.sort-asc .sort-arrow::after {
  content: ' ↑';
}

.lens-table th.sort-desc .sort-arrow {
  opacity: 1;
}

.lens-table th.sort-desc .sort-arrow::after {
  content: ' ↓';
}

.lens-table tbody tr {
  border-bottom: 1px solid var(--border);
  transition: background 0.2s;
}

.lens-table tbody tr:hover {
  background: #f9f9f9;
}

.lens-table td {
  padding: 1rem;
  border-bottom: 1px solid var(--border);
}

.lens-name {
  font-weight: 500;
}

.lens-name a {
  color: var(--primary);
  text-decoration: none;
}

.lens-name a:hover {
  text-decoration: underline;
  color: var(--secondary);
}

@media (max-width: 768px) {
  .lens-table {
    font-size: 0.9rem;
  }
  
  .lens-table th,
  .lens-table td {
    padding: 0.75rem 0.5rem;
  }
}
</style>

<script>
// Sortable table functionality
(function() {
  const table = document.getElementById('lensTable');
  if (!table) return;
  
  const headers = table.querySelectorAll('th[data-sort]');
  let currentSort = { column: null, direction: 'asc' };
  
  headers.forEach(header => {
    header.addEventListener('click', function() {
      const sortKey = this.dataset.sort;
      const tbody = table.querySelector('tbody');
      const rows = Array.from(tbody.querySelectorAll('tr'));
      
      // Determine sort direction
      if (currentSort.column === sortKey) {
        currentSort.direction = currentSort.direction === 'asc' ? 'desc' : 'asc';
      } else {
        currentSort.direction = 'asc';
      }
      currentSort.column = sortKey;
      
      // Remove sort classes from all headers
      headers.forEach(h => {
        h.classList.remove('sort-asc', 'sort-desc');
      });
      
      // Add sort class to current header
      this.classList.add('sort-' + currentSort.direction);
      
      // Sort rows
      rows.sort((a, b) => {
        let aVal, bVal;
        
        if (sortKey === 'title') {
          aVal = a.querySelector('.lens-name a').textContent.trim().toLowerCase();
          bVal = b.querySelector('.lens-name a').textContent.trim().toLowerCase();
        } else {
          const aCell = a.querySelector(`td[data-value]`);
          const bCell = b.querySelector(`td[data-value]`);
          const aCells = a.querySelectorAll('td');
          const bCells = b.querySelectorAll('td');
          const colIndex = Array.from(headers).indexOf(this);
          
          if (aCell && bCell && aCell.dataset.value && bCell.dataset.value) {
            aVal = aCell.dataset.value;
            bVal = bCell.dataset.value;
          } else {
            aVal = aCells[colIndex].textContent.trim();
            bVal = bCells[colIndex].textContent.trim();
          }
        }
        
        // Handle empty values
        if (aVal === '—') return 1;
        if (bVal === '—') return -1;
        
        // Parse numbers for weight and aperture
        if (sortKey === 'weight') {
          aVal = parseInt(aVal) || 0;
          bVal = parseInt(bVal) || 0;
        } else if (sortKey === 'aperture') {
          aVal = parseFloat(aVal.replace('f/', '').replace('f', '')) || 0;
          bVal = parseFloat(bVal.replace('f/', '').replace('f', '')) || 0;
        } else if (sortKey === 'focal_length') {
          // Handle focal lengths like "25mm" or "12-40mm"
          aVal = parseInt(aVal.split('-')[0]) || 0;
          bVal = parseInt(bVal.split('-')[0]) || 0;
        }
        
        // Compare
        if (typeof aVal === 'string') {
          return currentSort.direction === 'asc' 
            ? aVal.localeCompare(bVal)
            : bVal.localeCompare(aVal);
        } else {
          return currentSort.direction === 'asc' 
            ? aVal - bVal
            : bVal - aVal;
        }
      });
      
      // Re-append sorted rows
      rows.forEach(row => tbody.appendChild(row));
    });
  });
  
  // Filter functionality
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.addEventListener('click', function() {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      this.classList.add('active');
      
      const filter = this.dataset.filter.toLowerCase();
      document.querySelectorAll('.lens-row').forEach(row => {
        if (filter === 'all') {
          row.style.display = '';
        } else if (filter === 'weathersealed-yes') {
          row.style.display = row.dataset.weathersealed === 'yes' ? '' : 'none';
        } else if (filter === 'weathersealed-no') {
          row.style.display = row.dataset.weathersealed === 'no' ? '' : 'none';
        } else if (filter === 'autofocus-yes') {
          row.style.display = row.dataset.autofocus === 'yes' ? '' : 'none';
        } else if (filter === 'autofocus-no') {
          row.style.display = row.dataset.autofocus === 'no' ? '' : 'none';
        } else {
          const rowType = row.dataset.type ? row.dataset.type.toLowerCase() : '';
          row.style.display = (rowType === filter || rowType.includes(filter)) ? '' : 'none';
        }
      });
    });
  });
})();
</script>