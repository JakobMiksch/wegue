<template>
    <v-data-table
      dense
      :headers="headers"
      :items="records"
    ></v-data-table>
</template>

<script>
import { Mapable } from '../../mixins/Mapable';
import LayerUtil from '../../util/Layer';

export default {
  name: 'wgu-attributetable',
  mixins: [Mapable],
  methods: {
    onMapBound () {
      console.log('map bound');
      const layer = LayerUtil.getLayerByLid(this.layerId, this.map);
      const source = layer.getSource();

      // set records
      this.records = source.getFeatures().map(
        feature => feature.getProperties()
      );
      let keys = source.getFeatures()[0].getKeys();

      // TODO: this only works for the case that
      //       the geometry is named 'geometry'
      //       --> it might be better to check if the
      //           type of the property is valid for the table
      const filtered = keys.filter(
        key => key !== 'geometry'
      );
      let headers = [];
      filtered.forEachj(propertyName => {
        headers.push({
          text: propertyName,
          value: propertyName
        });
      });
      // TODO: set headers from config e.g. a mapping from "title to value"
      this.headers = headers;
    }
  },
  props: {
    layerId: {type: String, required: true}
  },
  data () {
    return {
      headers: [
        {
          text: 'Ort',
          value: 'NAME'
        },
        {
          text: 'Einwohner (Max)',
          value: 'POP_MAX'
        }
      ],
      records: []
    }
  }
}
</script>
