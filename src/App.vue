<template>
  <div id="app" class="container nodrama-container">
    <tiles></tiles>
  </div>
</template>

<script>
import Tiles from './components/Tiles.vue'
export default {
  name: 'app',
  components: {
    Tiles
  }
}
</script>

<style scoped>
  .nodrama-container {
    margin-top: 50px;
  }
</style>
