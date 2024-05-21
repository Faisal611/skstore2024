
```liquid
<!--- Search Field ---> 
        <form action="{{ routes.search_url }}">
          <div class="input-group">
            <input
              type="text"
              name="q"
              class="form-control"
              placeholder="Search"
              value="{{ search.terms | escape }}"
            >
            <button class="btn btn-outline-secondary" type="submit">
              Search
            </button>
          </div>
        </form>
        
<!--- Search Result ---> 
    <div class="search-results">
      <div class="row">
        {% for item in search.results %}
          {% case item.object_type %}
            {% when 'product' %}
            {%- render 'product-card', product: item -%}
            {% when 'article' %}
              {%- render 'article-card', article: item -%}
            {% when 'page' %}
              {%- render 'page-card', page: item -%}
          {% endcase %}
        {% endfor %}
      </div>
    </div>

```