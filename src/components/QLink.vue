<template>
  <div class="linkComponent">
    <!-- Intern link -->
    <template v-if="type === 'internal'">
      <!-- Force reload -->
      <template v-if="forceReload">
        <a @click="$emit('click')" :href="to" :title="linkTitle">
          <slot />
        </a>
      </template>

      <!-- Normal intern link -->
      <template v-else>
        <nuxt-link @click.native="$emit('click')" :to="to" :title="linkTitle">
          <slot />
        </nuxt-link>
      </template>
    </template>

    <!-- prevented link -->
    <template v-if="type === 'prevented'">
      <a @click.prevent.stop="$emit('click')" :title="linkTitle" href="#">
        <slot />
      </a>
    </template>

    <!-- External link -->
    <template v-if="type === 'external'">
      <a @click="$emit('click')" :href="to" :title="linkTitle" target="_blank" rel="noreferrer">
        <slot />
      </a>
    </template>

    <!-- Tel, Mail, place -->
    <template v-if="type === 'tel' || type === 'email' || type === 'place'">
      <no-ssr>
        <a
          @click="$emit('click')"
          :href="contactLink"
          :title="linkTitle"
          target="_blank"
          rel="noreferrer"
        >
          <slot />
        </a>
      </no-ssr>
    </template>
  </div>
</template>

<script>
const isOneOf = (value, ...possibilities) =>
  possibilities.some(possibility => possibility === value)

export default {
  props: {
    type: {
      type: String,
      required: true,
      validator: value => isOneOf(value, 'external', 'internal', 'email', 'tel', 'place', 'prevented'),
      default: 'internal'
    },
    forceReload: {
      type: Boolean,
      required: false,
      default: false
    },
    title: {
      type: String,
      required: false,
      default: ''
    },
    to: {
      type: [String, Object],
      required: false,
      default: '#'
    },
    tel: {
      type: String,
      required: false,
      default: null
    },
    email: {
      type: String,
      required: false,
      default: null
    },
    place: {
      type: String,
      required: false,
      default: null
    }
  },
  computed: {
    contactLink () {
      if (this.type === 'email') {
        return 'mailto:' + this.email
      }

      if (this.type === 'tel') {
        return 'tel:' + this.tel
      }

      if (this.type === 'place') {
        return 'https://www.google.com/maps/search/?api=1&query=' + encodeURI(this.place)
      }

      return ''
    },
    linkTitle () {
      if (this.title) {
        return this.title
      }

      if (this.type === 'email') {
        return `Envoyez un email à ${this.email}`
      }
      if (this.type === 'tel') {
        return `Appelez le ${this.tel}`
      }

      return 'Voir cette page'
    }
  }
}
</script>

<style>
a {
  display: inline-block;
  width: 100%;
  height: 100%;
}
</style>
