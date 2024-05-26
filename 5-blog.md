

Blog:https://shopify.dev/docs/api/liquid/objects/article
```liquid
    {% for article in blog.articles limit: section.settings.post_limit %}{%endfor%}
    {% for blog in blogs.news.articles %} {%endfor%}
    
    {{ article.title }}
    
    {{ 'blogs.article.by_author' | t: author: article.author }}
    
    {{ article.published_at | time_tag: format: 'month_day_year' }}
     
    {{ article.excerpt }}
```


Blog Content:
```liquid
 <div>
    {% if article.excerpt.size > 0 %}
      {{ article.excerpt }}
    {% else %}
      {{ article.content | strip_html | truncate: 150 }}
    {% endif %}
  </div>
```
Blog Tag:
```liquid
  {% if article.tags.size > 0 %}
    <ul aria-label="{{ 'blogs.article.tags' | t }}">
      {% for tag in article.tags %}
        <li><a href="{{ blog.url }}/tagged/{{ tag | handle }}">{{ tag }}</a></li>
      {% endfor %}
    </ul>
  {% endif %}
```
Blog Read More:
```liquid
  <a href="{{ article.url }}" aria-label="{{ 'blogs.article.read_more_title' | t: title: article.title }}">{{ 'blogs.article.read_more' | t }}</a>
```
