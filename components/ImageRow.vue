<template>
  <div class="image-row-ctn">
    <div v-for="(img, index) in images" :key="index" class="img-ctn">
      <img :src="img" alt="">
    </div>
    <div class="img-ctn">
      +{{users - 5}}
    </div>
  </div>
</template>

<script>
import images from '@/components/images.js'
export default {
  props: {
    users: {
      type: Number,
      default: () => 1
    }
  },
  data () {
    return {
      images
    }
  }
  
}
</script>

