---
drafts: false
date: 2024-04-29
---

# blog


For the API app to have its own urls.py to contain the paths for the API end points, we add the below to
`todobackend/backend/urls.py`:

<!-- more -->

!!! success "urls.py"

    ```bash
    from django.contrib import admin
    from django.urls import path, include

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('api/', include('api.urls')),
    ]
    ```

    This will forward all API related paths e.g. `localhost:8000/api/*` to the API app.

---

## Reference