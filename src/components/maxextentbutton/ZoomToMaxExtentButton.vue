<template>

  <v-btn icon :dark="dark" @click="onClick">
    <v-icon medium>{{icon}}</v-icon>
    {{text}}
  </v-btn>

</template>

<script>

import { Mapable } from '../../mixins/Mapable';

export default {
  name: 'wgu-zoomtomaxextent-btn',
  mixins: [Mapable],
  props: {
    icon: {type: String, required: false, default: 'zoom_out_map'},
    text: {type: String, required: false, default: ''},
    dark: {type: Boolean, required: false, default: false}
  },
  methods: {
    onClick () {
      // derive correct initial zoom and center
      const initialCenter = this.$appConfig.mapCenter;
      const initalZoom = this.$appConfig.mapZoom
      this.map.getView().setCenter(initialCenter);
      this.map.getView().setZoom(initalZoom);
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
