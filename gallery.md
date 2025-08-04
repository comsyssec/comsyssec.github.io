<h1>Gallery</h1>

<div class="gallery">
  {% for item in site.gallery %}
    <div class="gallery-item">
      <img src="{{ item.image }}" alt="{{ item.title }}" style="max-width: 300px;">
      <p><strong>{{ item.title }}</strong><br>{{ item.date }}</p>
      {{ item.content | markdownify }}
    </div>
  {% endfor %}
</div>
