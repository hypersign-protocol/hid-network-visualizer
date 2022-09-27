<template>
  <div class="">
    <v-network-graph
      ref="graph"
      :nodes="data.nodes"
      :edges="data.edges"
      :layouts="data.layouts"
      :configs="data.configs"
      :layers="layers"
    >
      <!-- Additional layer -->
      <template #worldmap>
        <image
          href="https://simplemaps.com/static/demos/resources/svg-library/svgs/world.svg"
          x="0"
          y="0"
          width="1000px"
          height="500px"
          @load="onLoadImage"
        />
      </template>
    </v-network-graph>
  </div>
</template>
<script setup lang="ts">
  import { ref } from "vue"
  import * as vNG from "v-network-graph"
  import data from "../views/data"
  
  // additional layers definition
  const layers = {
    // {layername}: {position}
    worldmap: "base",
  }
  
  // ref="graph"
  const graph = ref<vNG.Instance>()
  
  function onLoadImage() {
    graph.value?.fitToContents()
  }
  </script>



<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
