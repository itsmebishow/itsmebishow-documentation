## CSS

```css
.truncate {
  text-overflow: ellipsis;

  /* Needed to make it work */
  overflow: hidden;
  white-space: nowrap;
}
```

Nice nice, that’s a good start. But what if we want to introduce the ellipsis ==not on the first line== **but somewhere**, say, the third line of text?

That’s where line-clamp comes into play. Just note that a combination of three properties are used to make it happen:

```css
.line-clamp {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;  
  overflow: hidden;
}
```

---

### Reference

- [line-clamp](https://css-tricks.com/almanac/properties/l/line-clamp/)
- [-webkit-line-clamp](https://developer.mozilla.org/en-US/docs/Web/CSS/-webkit-line-clamp)

- [redis - outdated](https://github.com/microsoftarchive/redis)
- [redis](https://www.memurai.com/)

- [metro.co.uk](https://metro.co.uk/)



---

## CSS

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

### CSS Variables

The `var()` function is used to insert the value of a CSS variable.
