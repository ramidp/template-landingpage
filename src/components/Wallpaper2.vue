<script setup>

const prop = defineProps({
        theme: Object
          })


</script>

<template>

  <div class="wallpaper2-container">


  </div>

 
</template>

<style lang='scss' scoped>

.wallpaper2-container {
    width: 100%;
    height: 100%;
    position: fixed;
    background-image: url('wallpaper.jpg');
    background-size: cover;
    background-position: 50% 50%;
    background-repeat: no-repeat;
    z-index: -1;
  }


</style>
