<template>
  <div class="image-row-ctn">
    <div v-for="(img, index) in images" v-show="index <= users" :key="index" class="img-ctn">
      <img :src="require(`@/assets/images/pngs/${img}.png`)" alt="">
    <!-- <div class="img-ctn">
      +{{users > index ? users - 5 : ''}}
    </div> -->
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

<style scoped>
.image-row-ctn {
  display: flex;
}
</style>

