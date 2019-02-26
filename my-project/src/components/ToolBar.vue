<template>
  <div

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

      <v-toolbar-title>{{ title }}</v-toolbar-title>

      <v-spacer></v-spacer>

      <!--<v-btn icon>-->
        <!--<v-icon>search</v-icon>-->
      <!--</v-btn>-->

      <!--<v-btn icon>-->
        <!--<v-icon>favorite</v-icon>-->
      <!--</v-btn>-->

      <!--<v-btn icon>-->
        <!--<v-icon>more_vert</v-icon>-->
      <!--</v-btn>-->
    </v-toolbar>
  </div>
</template>

<script>
  import { EventBus } from '../assets/js/event-bus.js'

export default {
  name: 'ToolBar',
  data: function(){
    return {
      title: 'Home'
    }
  },
  methods: {
    toggleDrawer: function () {
      EventBus.$emit('toggleDrawer');
    },
    setTitle(title) {
      this.title = title;
    }
  },
  created() {
    EventBus.$on('setToolBarTitle', (title) => {
      this.setTitle(title);
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
