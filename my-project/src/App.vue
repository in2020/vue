<template>
  <v-app>
    <component :is="appComponent"></component>
  </v-app>
</template>

<script>
import Main from './components/Main'

export default {
  name: 'App',
  components: {
    Main
  },
  data () {
    return {
      appComponent: Main
    }
  }
}
</script>
