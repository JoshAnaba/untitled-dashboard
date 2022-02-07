<template>
  <div class="image-row-ctn">
    <div v-for="(img, index) in images.slice(0, 6)" v-show="index <= users" :key="index" class="img-ctn" :style="`z-index:${index}`">
      <img :src="require(`@/assets/images/pngs/${img}.png`)" alt="">
    </div>
    <div v-if="users>5" class="remaining-user-ctn" :style="`z-index: ${users+1}`">
      {{users>5 ? `+${users-5}` : ''}}
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
  position: relative;
}

.img-ctn {
  /* position: absolute; */
  max-width: 25px;
  min-width: 25px;
}

.img-ctn img {
  min-width: 35px;
  max-width: 35px;
  min-height: 35px;
  max-height: 35px;
  border: 1px solid transparent;
  border-radius: 50%;
}

.remaining-user-ctn {
  min-width: 34px;
  max-width: 34px;
  min-height: 34px;
  max-height: 34px;
  border: 2px solid #fff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--primary-purple);
  font-size: 13px;
  background: var(--purple-lightest);
  font-weight: 500;
}
</style>

