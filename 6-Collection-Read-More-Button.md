

Collection Load More Button:
```liquid
            <ul
             
              id="product-grid"
              data-next-url="{{ paginate.next.url }}"
              data-id="{{ section.id }}"
              class=" product-on-page
                grid product-grid grid--{{ section.settings.columns_mobile }}-col-tablet-down
                grid--{{ section.settings.columns_desktop }}-col-desktop
                {% if section.settings.quick_add == 'bulk' %} collection-quick-add-bulk{% endif %}
              "
            >
              {%- for product in collection.products -%}
                {% assign lazy_load = false %}
                {%- if forloop.index > 2 -%}
                  {%- assign lazy_load = true -%}
                {%- endif -%}
                <li
                  class="grid__item{% if settings.animations_reveal_on_scroll %} scroll-trigger animate--slide-in{% endif %}"
                  {% if settings.animations_reveal_on_scroll %}
                    data-cascade
                    style="--animation-order: {{ forloop.index }};"
                  {% endif %}
                >
                  {% render 'card-product',
                    card_product: product,
                    media_aspect_ratio: section.settings.image_ratio,
                    image_shape: section.settings.image_shape,
                    show_secondary_image: section.settings.show_secondary_image,
                    show_vendor: section.settings.show_vendor,
                    show_rating: section.settings.show_rating,
                    lazy_load: lazy_load,
                    quick_add: section.settings.quick_add,
                    section_id: section.id
                  %}
                </li>
              {%- endfor -%}
            </ul>
          
```
```js
var product_on_page =  $('.product-on-page');
var next_url = product_on_page.data('next-url')
function loadMoreProduct (){
    $.ajax(
        {
            url:next_url,
            type:'GET',
            dataType: 'html'
        }
    ).done(function (next_page){
        var new_products = $(next_page).find('.product-on-page');
        var new_url = new_products.data('next-url');

        next_url = new_url;

        product_on_page.append(new_products.html())
    });
}
```

