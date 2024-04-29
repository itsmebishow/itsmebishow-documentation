

!!! example "bootstrap order"

    ```python
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                <h1>{{ abouts.title }}</h1>
            </div>
            <div class="col-md-6 order-2 order-md-1">
                <p>{{ abouts.description }}</p>
            </div>
            <div class="col-md-6 order-1 order-md-2">
                {% if abouts.image %}
                    <img src="{{ abouts.image.url }}" alt="{{ abouts.title }}">
                {% endif %}
            </div>
        </div>
    </div>
    ```

## CSS Variables

The `var()` function is used to insert the value of a CSS variable.
