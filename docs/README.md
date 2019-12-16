# Introduction

Nuxt component for links

## Install

```bash
yarn add @qneyraud/q-link
```

## Usage

```js
import QLink from '@qneyraud/q-link'
import '@qneyraud/q-link/dist/QLink.css'

// or
import QLink from '@qneyraud/q-link/src/components/QLink'


export default {
  components: {
    QLink
  }
}
```

## Development

```
# clone repo
git clone git@github.com:quentinneyraud/q-link.git
cd q-link

# install dependencies
yarn

# Run example
npm run serve
```

## Build

```bash
npm run build-bundle
```

<div style="margin-top:200px"></div>

# Options

## type

> Define behavior of the link 
> 
> `internal`: Basic nuxt-link  
> `external`: Basic link with `target="_blank"`  
> `email`: mailto link (use no-ssr to prevent crawling)  
> `tel`: tel link (use no-ssr to prevent crawling)  
> `place` will open `https://www.google.com/maps/search/?api=1&query=` with `place` property in query
> `prevented` Basic link with click prevented and propagation stopped

**Type**: String   
**Required**: true   
**Default**: 'internal' 

## forceReload

> Force page reloading for `internal` type links   

**Type**: Boolean   
**Required**: false   
**Default**: false 

## title

> Title attribute of the link

**Type**: String   
**Required**: false   
**Default**: created from `type` and `text` properties

## to

> href attribute of the link 

**Type**: String   
**Required**: false   
**Default**: `#`

## tel

> tel number if `type` is `tel`

**Type**: String   
**Required**: false   
**Default**: null 

## email

> email if `type` is `email`

**Type**: String   
**Required**: false   
**Default**: null 

## place

> place passed in google maps query if `type` is `place`

**Type**: String   
**Required**: false   
**Default**: null 

<div style="margin-top:200px"></div>


# Events

## click

> Emitted when the user click the link

**Parameter**: MouseEvent

<div style="margin-top:200px"></div>

# Examples

## Internal link

```vue
<q-link 
  type="internal"
  to="contact"
  title="Go to Contact page">
</q-link>
```

## Internal link with page refresh

```vue
<q-link 
  type="internal"
  :forceReload="true"
  to="contact"
  title="Go to Contact page">
</q-link>
```

## External link

```vue
<q-link 
  type="external"
  to="/prices.pdf"
  title="View our prices">
</q-link>
```

## Email link

```vue
<q-link 
  type="email"
  email="quentin@akaru.fr"
  title="Send an email to quentin@akaru.fr">
</q-link>
```

## Tel link

```vue
<q-link 
  type="tel"
  tel="911"
  title="Call 911">
</q-link>
```

## Place link

```vue
<q-link 
  type="place"
  place="9, quai André Lassagne"
  title="Go to office">
</q-link>
```

## Prevented link

```vue
<template>
  <q-link 
    type="prevented"
    title="Open this modal"
    @click="onModalClick">
  </q-link>
</template>

<script>
  export default {
    methods: {
      onModalClick () {
        // modal.open()
      }
    }
  }
</script>
```
