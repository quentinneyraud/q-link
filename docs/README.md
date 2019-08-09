# Introduction

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

<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

# Options

## type

> Define behavior of the link 
> 
> `internal`: Basic nuxt-link  
> `external`: Bascic link with `target="_blank"`  
> `email`: mailto link (use no-ssr to prevent crawling)
> `tel`: tel link (use no-ssr to prevent crawling)
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

<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>


# Events

## click

> Emitted when the user click the link

**Parameter**: MouseEvent

<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

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
