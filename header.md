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
<!-- Currency Area End -->

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
````
Languages Function:
https://shopify.dev/docs/themes/markets/multiple-currencies-languages#the-language-selector
````

<!--- Language Area Start --->
    {% if settings.enable_language_selector %}
        {% if localization.available_languages.size > 1 %}
            <div class="lang-area">
               {% form 'localization' %}
                   <select name="language_code" id="" class="language_selector">
                       {% for language in localization.available_languages %}
                           {% if language.iso_code == localization.language.iso_code %}
                                <option value="{{ language.iso_code }}" selected> {{ language.endonym_name | capitalize }}</option>
                           {% else %}
                                <option value="{{ language.iso_code }}"> {{ language.endonym_name | capitalize }}</option>
                       {% endif %}
                       {% endfor %}
                   </select>
                   {% comment %}<button type="submit">submit</button>{% endcomment %}
                {% endform %}
            </div>
        {% endif %}
    {% endif %}
<!--- Language Area End --->
````