
Footer menu link
```liquid
{% for block in section.blocks %}
  {% case block.type %}
    {% when 'menu' %}
      <div class="{{ column }}">
        <h2>{{ block.settings.title }}</h2>
        <div class="footer_link">
          <ul>
            {% for link in block.settings.footer_menu.links %}
              <li>
                <a href="{{ link.url }}">{{ link.title }}</a>
              </li>
            {% endfor %}
          </ul>
        </div>
      </div>
    {% endcase %}
  {% endfor %}
```
Footer Image
```liquid
{% for block in section.blocks %}
  {% case block.type %}
    {% when 'image_title' %}
      <div class="{{ column }}">
        <div class="image-text">
          <h4>{{ block.settings.img_title }}</h4>
          <div class="footer-img">
            <a href="{{ block.settings.img_link }}">
              <img src="{{ block.settings.footer_img | img_url:'medium'}}" width="100%" alt="Footer image">
            </a>
          </div>
        </div>
      </div>
  {% endcase %}
{% endfor %}
```
column
```liquid
{% liquid

  case section.blocks.size
    when 1
      assign column = 'col-lg-12 col-md-12 col-sm-12'
    when 2
      assign column = 'col-lg-6 col-md-6 col-sm-12'
    when 3
      assign column = 'col-lg-4 col-md-4 col-sm-6'
    when 4
      assign column = 'col-lg-3 col-md-3 col-sm-6'
   else
      assign column = 'col-12'
   endcase
%}
```
Block Schema
```liquid
{% schema %}
{
  "name": "Section Footer",
  "settings": [],
  "blocks": [
    {
      "type": "menu",
      "name": "Footer Menu",
      "limit": 4,
      "settings": [
        {
          "type": "text",
          "id": "title",
          "label": "Title"
        },
        {
          "type": "link_list",
          "id": "footer_menu",
          "label": "Footer Menu"
        }
      ]
    },
    {
      "type": "image_title",
      "name": "Image Title",
      "limit": 1,
      "settings": [
        {
          "type": "text",
          "id": "img_title",
          "label": "Title"
        },
        {
          "type": "image_picker",
          "id": "footer_img",
          "label": "Footer image"
        },
        {
          "type": "url",
          "id": "img_link",
          "label": "link"
        }

      ]
    }
  ],
  "presets": [
    {
      "name": "Footer Area",
      "category": "footer"
    }
  ]
}
{% endschema %}

```