<template>
  <v-data-table
    v-if=show
    dense
    :headers="headers"
    :items="features"
    item-key="name"
    class="elevation-1"
  ></v-data-table>
</template>

<script>

import { Mapable } from '../../mixins/Mapable';

export default {
  name: 'wgu-attributetable-win',
  mixins: [Mapable],

  methods: {
    onMapBound: function () {
      console.log('map ready in attribute table');
    }
  },

  data: () => ({
    show: false,
    headers: [
      {
        text: 'Ort',
        align: 'start',
        sortable: false,
        value: 'NAME'
      },
      { text: 'Einwohner (Max)', value: 'POP_MAX' }
    ],
    features: [
      {
        'NAME': 'Vatican City',
        'ADM0NAME': 'Vatican (Holy See)',
        'POP_MAX': 832,
        'TIMEZONE': 'Europe/Vatican'
      },
      {
        'NAME': 'San Marino',
        'ADM0NAME': 'San Marino',
        'POP_MAX': 29579,
        'TIMEZONE': 'Europe/San_Marino'
      },
      {
        'NAME': 'Vaduz',
        'ADM0NAME': 'Liechtenstein',
        'POP_MAX': 36281,
        'TIMEZONE': 'Europe/Vaduz'
      }
    ]
  })
}

</script>

<style scoped>
.position {
  position: absolute;
  top: 64px;
  left: 16px;
  z-index: 2;
}
</style>
