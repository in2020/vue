<template>
  <div>
    <side-drawer
      @switch-body="switchBody"
    ></side-drawer>
    <tool-bar></tool-bar>
    <div
            id="scrolling-techniques"
            class="scroll-y"
            style="margin-top: 56px; max-height: 600px;"
    >
      <v-container style="min-height: 500px">
        <component :is="body" @switch-body="switchBody"></component>
      </v-container>
    </div>
  </div>
</template>

<script>
  import SideDrawer from './SideDrawer'
  import ToolBar from './ToolBar'
  import Home from './Home'

export default {
  name: 'Home',
  data: function(){
    return {
      body: Home
    }
  },
  methods:{
    switchBody: function(component){
      this.body = component;
    }
  },
  components: {
    SideDrawer,
    ToolBar
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
