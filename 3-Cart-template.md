
Header Cart
```liquid
<div class="cart-counter mx-5">
    <a class="" href="{{ routes.cart_url }}">
        {% if cart.item_count > 0 %}
            <span class="shopping-bag">{% render 'icons', icon: 'bag-fill' %}</span>
            (<span> {{ cart.item_count }} </span>)
        {% else %}
            <span class="shopping-bag">{% render 'icons', icon: 'bag' %}</span>
        {% endif %}
    </a>
</div>
```
Cart template image:
```liquid
{% for line_item in cart.items %}
  <div class="item-image px-2">
    {% if line_item.image != empty %}
      <img
        src="{{ line_item.image | image_url:width:300 }}"
        width="100"
        height="auto"
        alt="Photo"
      >
    {% endif %}
  </div>
{% endfor %}
``` 
```liquid
{% for line_item in cart.items %}
    <!-- product  name/price show  -->
    <p>{{ line_item.product.title | link_to: line_item.url }}</p>
    <div class="price">
      <span>Price: {{ line_item.original_price | money }}</span>
    </div>
{% endfor %}
```
Product variant name show:
```liquid
{% for line_item in cart.items %} 
<!-- product variant name show start -->
    {% if line_item.product.has_only_default_variant == false
    or line_item.properties.size != 0
    or line_item.selling_plan_allocation != null
    %}
        {% if line_item.product.has_only_default_variant == false %}
        <div class="item-optiona">
          {% for option in line_item.options_with_values %}
            <span>{{ option.name | escape }}: {{ option.value }}</span><br>
          {% endfor %}
        </div>
        {% endif %}
    {% endif %}
<!-- product variant name show end -->
{% endfor %}
```
Product Price:
```liquid
<!-- product Price -->
{% for line_item in cart.items %} 
    <div class="price-wrapper">
      {% if line_item.original_price != line_item.final_price %}
         <del>{{ line_item.original_price | money }}</del><br>
        <span class="final-sale-price">{{ line_item.final_line_price | money }}</span>
      {% else %}
        <span class="final-original-price">{{ line_item.original_price | money }}</span>
      {% endif %}
    </div>
    
    <!-- product Total Price -->
    <div class="final-price-wrapper">
      {% if line_item.original_line_price != line_item.final_line_price %}
        <del>{{ line_item.original_line_price | money }}</del><br>
        <span class="final-sale-price">{{ line_item.final_line_price | money }}</span>
      {% else %}
        <span class="final-original-price">{{ line_item.original_line_price | money }}</span>
      {% endif %}
    </div>
{% endfor %}
```
Product quantity: 
```liquid
{% for line_item in cart.items %}
    <div class="quantity-area">
      <div class="input-group mb-3" style="width: 150px">
        <div class="input-group-prepend">
          <a
            href="/cart/change?line={{ forloop.index }}&quantity={{ line_item.quantity | minus: 1 }}"
            class="nav-link input-group-text"
            >-</a
          >
        </div>
        <input
          type="number"
          class="form-control"
          name="updates[]"
          value="{{ line_item.quantity }}"
        >
        <div class="input-group-append">
          <a
            href="/cart/change?line={{ forloop.index }}&quantity={{ line_item.quantity | plus: 1 }}"
            class="nav-link input-group-text {% if line_item.variant.inventory_quantity == line_item.quantity %}disabled{% endif %}">+
          </a>
        </div>
      </div>
    </div>
{% endfor %}

```
Cart Product Remove
```liquid
{% for line_item in cart.items %}
    <div class="item-remove">
      <a href="{{ line_item.url_to_remove }}" class="nvd-link">
        <span class="remove-icon">{% render 'icons' icon:'trash' %}</span>
      </a>
    </div>
{% endfor %}
```
Sub Total :
```liquid
  <div class="card">
    <div class="card-body">
      <div class="cart-info d-flex justify-content-between">
        <strong>Sub Total</strong>
        <strong class="cart-subtotal">{{ cart.total_price | money_with_currency }}</strong>
      </div>

      <hr class="my-3">

      <div class="cart-note">
        <label>Note:</label>
        <textarea class="form-control" name="note">{{ cart.note }}</textarea>
      </div>

      <div class="cart-actions">
        <button type="submit" name="update" class="btn btn-primary w-100 my-2">
          {{ 'cart.general.update' | t }}
        </button>
        <button type="submit" name="checkout" class="btn btn-secondary w-100">
          {{ 'cart.general.checkout' | t }}
        </button>
      </div>
    </div>
  </div>
</div>
```