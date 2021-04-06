# Redirect route triggered simply by having a router-link reference it.

## Reproduce

* `npm run serve` the repo
* navigate to localhost:8080/spa/about (/spa is the router base)
* browser will be redirected to `/` infinitely because of the `router-link` referencing a redirect route

## Expected
The route redirect function will only be run on link click

## Actual
The route redirect function is being run on load

## Workaround
```
  {
    path: "/",
    beforeEnter() {
      window.location.href = "/";
    }
  }
```

## Context
I have a project where `domain.com/` is a static site. The Vue SPA is being served on `domain.com/base`. However, there is no content directly on `/base`, but only on `/base/something` Therefore, if someone tries to access `/base` the best user experience is to redirect them out of the SPA ecosystem back to `domain.com/`. To do this, the `/` route is set to redirect with `location.href = '/'`, but that is being triggered immediately when a `router-link` references that route, even if the user doesn't click it.


# router-test

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
