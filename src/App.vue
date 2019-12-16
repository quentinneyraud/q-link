<template>
  <div id="app">
    <!-- Internal -->
    <q-link v-bind="link1" class="app-link">
      My link
    </q-link>

    <!-- Internal - force reload -->
    <q-link v-bind="link2" class="app-link">
      My link
    </q-link>

    <!-- External -->
    <q-link v-bind="link3" class="app-link">
      My link
    </q-link>

    <!-- Email -->
    <q-link v-bind="link4" class="app-link">
      My link
    </q-link>

    <!-- Tel -->
    <q-link v-bind="link5" class="app-link">
      My link
    </q-link>

    <!-- Tel -->
    <q-link v-bind="link6" class="app-link">
      My link
    </q-link>

    <!-- Prevented -->
    <q-link v-bind="link7" @click="onModalClick" class="app-link">
      My link
    </q-link>
  </div>
</template>

<script>
import QLink from './components/QLink.vue'

export default {
  name: 'App',
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
        type: 'place',
        place: '9, quai André Lassagne',
        title: 'Go to Akaru'
      },
      link7: {
        type: 'prevented',
        title: 'Open this modal'
      }
    }
  },
  methods: {
    onModalClick () {
      // modal.open()
    }
  }
}
</script>

<style scoped>
  html, body {
    margin: 0;
    padding: 0;
  }
  .app-link {
    width: 100px;
    height: 50px;
  }
</style>
