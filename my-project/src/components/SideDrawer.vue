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
          <v-list-tile-title>Snaps</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>

    <v-list class="pt-0" dense>
      <v-divider></v-divider>

      <v-list-tile
              v-for="item in items"
              :key="item.title"
              @click="clickItem(item)"
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
  import Snaps from './Snaps'
  import { EventBus } from '../assets/js/event-bus.js'

export default {
  name: 'SideDrawer',
  data: function(){
    return {
      drawer: false,
      items: [
        { title: 'Home', icon: 'home', component: Home },
        { title: 'Snaps', icon: 'camera_alt', component: Snaps },
        { title: 'About', icon: 'business', component: About }
      ]
    }
  },
  methods:{
    clickItem: function(item){
      this.drawer = false;
      EventBus.$emit('setToolBarTitle', item.title);
      this.$emit('switch-body', item.component);
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
