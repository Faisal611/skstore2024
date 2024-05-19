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
