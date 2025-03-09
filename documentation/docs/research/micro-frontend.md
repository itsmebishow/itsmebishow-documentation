## Installation

```
npm install --global create-single-spa

# or

yarn global add create-single-spa
```

Then run the following:

> create-single-spa

```
npm init single-spa

#
npm init single-spa

# or

npx create-single-spa

# or

yarn create single-spa
```

---

## Decision Framework

To summarize, the micro-frontends decisions framework is composed of ==four key decisions==:

1. identifying,
2. composing,
3. routing, &
4. communicating.

![micro frontent decision framework](../assets/micro-frontend/micro-frontend-decision%20-framework.png)

### Routing Micro-Frontends

We won’t have any scalability issue in either case. The **client-side routing** ==is highly recommended== when your teams have stronger frontend skills so that it becomes natural having a client-side routing over a backend configuration.

---

## Reference

- [create-single-spa](https://single-spa.js.org/docs/create-single-spa)
- [Building Micro-Frontends by Luca Mezzalira](https://www.oreilly.com/library/view/building-micro-frontends/9781492082989/)
