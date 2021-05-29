<template>
  <div style="display: none;">
    <slot v-if="ready"></slot>
  </div>
</template>

<script>
import { DomEvent } from 'leaflet'
import {findRealParent, propsBinder} from "vue2-leaflet";
require("leaflet-velocity");

export default {
    name: "LVelocityLayer",
    props: {
        options: {
            type: Object
        },
    },
    data() {
        return {
            ready: false
        }
    },
    mounted() {
        this.mapObject = L.velocityLayer(this.options)
        DomEvent.on(this.mapObject, this.$listeners)
        propsBinder(this, this.mapObject, this.$options.props)
        this.ready = true
        this.parentContainer = findRealParent(this.$parent)
        this.mapObject.addTo(this.parentContainer.mapObject)
    },
    beforeDestroy() {
      this.parentContainer.removeLayer(this);
    },
}
</script>
