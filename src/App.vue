<template>
  <div id="app">
    <!-- Internal -->
    <q-link
      class="app-link"
      v-bind="link1">
      My link
    </q-link>

    <!-- Internal - force reload -->
    <q-link
      class="app-link"
      v-bind="link2">
      My link
    </q-link>

    <!-- External -->
    <q-link
      class="app-link"
      v-bind="link3">
      My link
    </q-link>

    <!-- Email -->
    <q-link
      class="app-link"
      v-bind="link4">
      My link
    </q-link>

    <!-- Tel -->
    <q-link
      class="app-link"
      v-bind="link5">
      My link
    </q-link>

    <!-- Prevented -->
    <q-link
      class="app-link"
      v-bind="link6"
      @click="onModalClick">
      My link
    </q-link>
  </div>
</template>

<script>
import QLink from './components/QLink.vue'

export default {
  name: 'app',
  components: {
    QLink
  },
  data () {
    return {
      link1: {
        type: 'internal',
        to: 'contact',
        title: 'Go to Contact'
      },
      link2: {
        type: 'internal',
        forceReload: true,
        to: '',
        title: 'Reload page'
      },
      link3: {
        type: 'external',
        to: '/prices.pdf',
        title: 'View our prices'
      },
      link4: {
        type: 'email',
        email: 'quentin@akaru.fr',
        title: 'Send email to quentin@akaru.fr'
      },
      link5: {
        type: 'tel',
        tel: '911',
        title: 'Call 911'
      },
      link6: {
        type: 'prevented',
        title: 'Open this modal'
      },
    }
  },
  methods: {
    onModalClick () {
      // modal.open()
    }
  }
}
</script>

<style lang="stylus">
  html, body
    margin 0
    padding 0
</style>

<style lang="stylus" scoped>
.app-link
  width 100px
  height 50px
</style>
