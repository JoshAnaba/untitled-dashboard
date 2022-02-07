<template>
  <div>
    <div v-if="checked" class="checkbox checked" @click="toggleCheck()">
      <div v-if="!header" class="material-icons-round">
        check
      </div>
      <div v-else class="material-icons-round">
        remove
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
    },
    header: {
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
  min-width: 20px;
  max-width: 20px;
  height: 20px;
  max-height: 20px;
  border: 1px solid #D0D5DD;
  border-radius: 6px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  user-select: none;
}

.checkbox .material-icons-round,
.checkbox .material-icons,
.checkbox .material-icons-outlined {
  color: var(--primary-purple);
  font-size: 16px;
  font-weight: 700;
  user-select: none;
}

.checkbox.checked {
  border: 1px solid var(--primary-purple);
}
</style>