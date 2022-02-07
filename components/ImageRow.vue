<template>
  <div class="image-row-ctn">
    <div v-for="(img, index) in images" :key="index" class="img-ctn">
      <img v-show="index <= users" :src="require(`@/assets/images/pngs/${img}.png`)" alt="">
    </div>
    {{users>5 ? `+${users-5}` : ''}}
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

<style scoped>
.image-row-ctn {
  display: flex;
}
</style>

