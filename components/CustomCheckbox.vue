<template>
  <div>
    <div v-if="checked" class="checkbox checked" @click="toggleCheck()">
      <div class="material-icons">
        check
      </div>
    </div>
    <div v-else class="checkbox" @click="toggleCheck()" />
  </div>
</template>

<script>
export default {
  props: {
    checked: {
      type: Boolean,
      default: () => false
    }
  },
  data () {
    return {
      // checked: false
    }
  },
  methods: {
    toggleCheck () {
      // this.checked = !this.checked
      this.$emit('toggle-check')
    }
  }
}
</script>

<style scoped>
.checkbox {
  min-width: 25px;
  max-width: 25px;
  height: 25px;
  max-height: 25px;
  border: 1px solid #D0D5DD;
  border-radius: 5px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  user-select: none;
}

.checkbox .material-icons {
  color: var(--primary-purple);
  font-size: 17px;
  font-weight: 700;
  user-select: none;
}

.checkbox.checked {
  border: 1px solid var(--primary-purple);
}
</style>