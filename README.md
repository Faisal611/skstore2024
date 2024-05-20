Header
````
<!-- Menu area Start -->
<ul class="navbar-nav me-auto mb-2 mb-lg-0">
    {% for link in menu.links %}
        <li class="nav-item {% if link.links.size > 0 %}dropdown{% endif %}">
            <a
                    class="nav-link active {% if link.links.size > 0 %}dropdown-toggle{% endif %}"
                    aria-current="page"
                    href="{{ link.url }}"
                    {% if link.links.size > 0 %}
                        role="button" data-bs-toggle="dropdown" aria-expanded="false"
                    {% endif %}
            >
                {{ link.title }}
            </a>

            <!-- Sub Menu area Start -->
            {% if link.links.size > 0 %}
                <ul class="dropdown-menu">
                    {% for dropdown in link.links %}
                        <li>
                            <a class="dropdown-item"
                               href="{{ dropdown.url }}">{{ dropdown.title }}</a>
                        </li>
                    {% endfor %}
                </ul>
            {% endif %}
            <!-- Sub Menu area End -->
        </li>
    {% endfor %}
</ul>
<!-- Menu area End -->
````
Currency Function
````
<!-- Currency Area Start -->
{% if settings.enable_currency_selector %}
    {% form 'currency' %}
        {{ form | currency_selector }}
    {% endform %}
{% endif %}

<!-- Currency Area Start -->
    {% if settings.enable_currency_selector %}
        <div class="currency_area mx-2">
            {% form 'currency' %}
                <select name="currency" id="" class="shopify-currency-form">
                    {% for currency in shop.enabled_currencies %}
                        {% if currency == cart.currency %}
                            <option value="{{ currency.iso_code }}"
                                    selected>{{ currency.symbol }} {{ currency.iso_code }}</option>
                        {% else %}
                            <option value="{{ currency.iso_code }}">{{ currency.iso_code }}</option>
                        {% endif %}
                    {% endfor %}
                </select>
            {% endform %}
        </div>
    {% endif %}
<!-- Currency Area End -->

<!-- Currency Area End -->
````
