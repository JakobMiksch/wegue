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
        value: 'properties.NAME'
      },
      {
        text: 'Einwohner (Max)',
        value: 'properties.POP_MAX'
      }
    ],
    features: [
      {
        'type': 'Feature',
        'properties': {
          'NAME': 'Vatican City',
          'ADM0NAME': 'Vatican (Holy See)',
          'POP_MAX': 832,
          'TIMEZONE': 'Europe/Vatican'
        },
        'geometry': {
          'type': 'Point',
          'coordinates': [
            12.453386544971766,
            41.903282179960115
          ]
        }
      },
      {
        'type': 'Feature',
        'properties': {
          'NAME': 'San Marino',
          'ADM0NAME': 'San Marino',
          'POP_MAX': 29579,
          'TIMEZONE': 'Europe/San_Marino'
        },
        'geometry': {
          'type': 'Point',
          'coordinates': [
            12.441770157800141,
            43.936095834768004
          ]
        }
      },
      {
        'type': 'Feature',
        'properties': {
          'NAME': 'Vaduz',
          'ADM0NAME': 'Liechtenstein',
          'POP_MAX': 36281,
          'TIMEZONE': 'Europe/Vaduz'
        },
        'geometry': {
          'type': 'Point',
          'coordinates': [
            9.516669472907267,
            47.133723774293571
          ]
        }
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
