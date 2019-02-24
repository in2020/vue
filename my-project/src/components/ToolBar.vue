<template>
  <div
          class="hide-overflow"
          style="position: relative;"
  >
    <v-toolbar
            absolute
            color="teal lighten-3"
            dark
            scroll-off-screen
            scroll-target="#scrolling-techniques"
    >
      <v-toolbar-side-icon
              @click.stop="toggleDrawer"
      ></v-toolbar-side-icon>

      <v-toolbar-title>Title</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>search</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>favorite</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>more_vert</v-icon>
      </v-btn>
    </v-toolbar>
    <div
            id="scrolling-techniques"
            class="scroll-y"
            style="margin-top: 56px; max-height: 600px;"
    >
      <v-container style="min-height: 500px">
        <component :is="body"></component>
      </v-container>
    </div>
  </div>
</template>

<script>
  import { EventBus } from '../assets/js/event-bus.js'

export default {
  name: 'ToolBar',
  props: {
    body: {
      type: Object,
      required: true
    }
  },
  data: function(){
    return {

    }
  },
  methods: {
    toggleDrawer: function () {
      EventBus.$emit('toggleDrawer');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
