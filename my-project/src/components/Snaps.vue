<template>
  <v-expansion-panel>
    <v-expansion-panel-content
            v-for="(item,i) in 5"
            :key="i"
    >
      <div slot="header">Item</div>
      <component :is="itemComponent" v-bind="{snap: item}"></component>
    </v-expansion-panel-content>
  </v-expansion-panel>
</template>

<script>
import Snap from './Snap'

export default {
  name: 'Snaps',
  data: function(){
    return {
      itemComponent: Snap,
      items: [
        {
          action: 'local_activity',
          title: 'Attractions',
          items: [
            { title: 'List Item' }
          ]
        },
        {
          action: 'restaurant',
          title: 'Dining',
          active: true,
          items: [
            { title: 'Breakfast & brunch' },
            { title: 'New American' },
            { title: 'Sushi' }
          ]
        },
        {
          action: 'school',
          title: 'Education',
          items: [
            { title: 'List Item' }
          ]
        },
        {
          action: 'directions_run',
          title: 'Family',
          items: [
            { title: 'List Item' }
          ]
        },
        {
          action: 'healing',
          title: 'Health',
          items: [
            { title: 'List Item' }
          ]
        },
        {
          action: 'content_cut',
          title: 'Office',
          items: [
            { title: 'List Item' }
          ]
        },
        {
          action: 'local_offer',
          title: 'Promotions',
          items: [
            { title: 'List Item' }
          ]
        }
      ]
    }
  },
  methods: {
    showSnap() {
      this.$emit('switch-body', Snap);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
