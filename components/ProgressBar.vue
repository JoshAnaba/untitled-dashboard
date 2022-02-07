<template>
  <div class="progress-bar-ctn">
    <div class="progress-content">
      <div class="progress__bar">
        <div
          v-for="index in overview"
          :key="index"
          :style="{ width: `calc(100%/${overview})`}"
          class="bar-container"
        >
          <div
            v-if="index <= currentProgress"
            :class="`${index === 1 ? 'first-bar' : ''} ${index === currentProgress ? 'last-bar' : ''}`"
            class="bar completed"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProgressBar',
  props: {
    overview: {
      type: Number,
      default: () => 5,
    },
    currentProgress: {
      type: Number,
      default: () => 1,
    }
  }
}
</script>

<style scoped>

.progress-bar-ctn {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 15px;
  font-weight: 500;
  position: sticky;
  top: 0;
  /* animation: come-down .5s ease-in-out; */
  /* -webkit-animation: come-down .5s ease-in-out; */
}

.progress-content {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 6px;
  font-weight: 500;
}

.progress-bar-ctn > p {
  text-transform: uppercase;
}

.progress-content > span {
  margin-left: auto;
}

.progress__bar {
  display: flex;
  width: 100%;
  height: 8px;
  background: var(--purple-lightest);
  border-radius: 5px;
}

.bar-container {
  max-width: 100%;
  height: 100%;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  background: transparent;
  border-radius: 0px;
}

.bar {
  height: 100%;
  background: transparent;
}

.last-bar {
  animation: fillBar 1s ease forwards !important;
  animation-delay: 1s;
  transform: 0.3;
}

@keyframes fillBar {
  0% {
    width: 0;
  }
  100% {
    width: 100%;
  }
}

.bar-container * {
  width: 100%;
}

.bar-container span {
  text-align: center;
  position: absolute;
  width: 100%;
  bottom: -61px;
  color: inherit;
}

.completed {
  color: var(--primary-purple);
  background: var(--primary-purple);
}

.first-bar {
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
}

.last-bar {
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}
</style>