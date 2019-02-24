<template>
  <v-navigation-drawer
          v-model="drawer"
          absolute
          temporary
  >
    <v-list class="pa-1">
      <v-list-tile avatar>
        <v-list-tile-avatar>
          <img src="https://randomuser.me/api/portraits/men/85.jpg">
        </v-list-tile-avatar>

        <v-list-tile-content>
          <v-list-tile-title>John Leider</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>

    <v-list class="pt-0" dense>
      <v-divider></v-divider>

      <v-list-tile
              v-for="item in items"
              :key="item.title"
              @click="clickItem(item.component)"
      >
        <v-list-tile-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-tile-action>

        <v-list-tile-content>
          <v-list-tile-title>{{ item.title }}</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
  import Home from './Home'
  import About from './About'
  import { EventBus } from '../assets/js/event-bus.js'

export default {
  name: 'SideDrawer',
  data: function(){
    return {
      drawer: false,
      items: [
        { title: 'Home', icon: 'dashboard', component: Home },
        { title: 'About', icon: 'question_answer', component: About }
      ]
    }
  },
  methods:{
    clickItem: function(component){
      this.drawer = false;
      this.$emit('switch-body', component);
    },

    toggleDrawer: function(){
      this.drawer = !this.drawer
    }
  },
  created: function(){
    EventBus.$on('toggleDrawer', () => {
      this.toggleDrawer();
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
