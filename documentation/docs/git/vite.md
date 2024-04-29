# Env Variables and Modes

## Env Variables

Vite exposes env variables on the special import.meta.env object. Some built-in variables are available in all cases:

- `import.meta.env.MODE`
- `import.meta.env.BASE_URL`
- `import.meta.env.PROD`
- `import.meta.env.DEV`
- `import.meta.env.SSR`

```
# .env.production

VITE_APP_TITLE=My App

# App.js

console.log(import.meta.env.VITE_APP_TITLE)
```

This code should be added inside eslintConfig:

```
"rules": {
    "no-unused-vars": "off"
}
```

---

#### Reference

- [Env Variables and Modes : Vite](https://vitejs.dev/guide/env-and-mode)
- [Vue: disable no-unused-vars error: the simplest fix](https://stackoverflow.com/questions/61874994/vue-disable-no-unused-vars-error-the-simplest-fix)
