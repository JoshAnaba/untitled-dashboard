<template>
  <div class="card-ctn">
    <div class="top">
      <div class="lhs">
        <p>
          {{details.name}}
        </p>
      </div>
      <div class="rhs">
        <span class="material-icons-outlined">
          more_vert
        </span>
      </div>
    </div>
    <div class="bottom">
      <div class="lhs">
        <h1>{{details.metric}}</h1>
        <div class="stats">
          <span :class="`material-icons-outlined ${details.rise ? 'upward' : 'downward'}`">
            arrow_{{details.rise ? 'upward' : 'downward'}}
          </span>
          <span :class="(details.rise ? 'upward' : 'downward')">
            {{details.value}}%
          </span>
          <span>
            vs last month
          </span>
        </div>
      </div>
      <div class="rhs">
        <img :src="require(`@/assets/images/pngs/${details.rise ? 'up' : 'down'}Chart.png`)" alt="">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    details: {
      type: Object,
      default: () => {
        return {

        }
      }
    }
  }
}
</script>

<style scoped>
.card-ctn,
.top,
.bottom,
.stats {
  display: flex;
}

.card-ctn {
  border: 1px solid var(--border-one);
  border-radius: 8px;
  padding: 20px;
  flex-direction: column;
  gap: 30px;
  min-height: 170px;
  min-width: 25%;
}

.top {
  justify-content: space-between;
}

.top .lhs p {
  font-size: 16px;
  font-weight: 400;
  color: var(--gray-dark);
}

.top .material-icons-outlined {
  cursor: pointer;
}

.upward {
  color: #12B76A;
}

.downward {
  color: #F04438;
}

.stats {
  align-items: center;
  gap: 5px
}

.stats span {
  font-size: 14px;
}

.stats span:last-child {
  color: var(--gray-light);
}

.bottom {
  justify-content: space-between;
  gap: 30px;
}

.bottom .lhs h1 {
  margin-bottom: 10px;
  color: var(--gray-darker);
}

.bottom .rhs {
  display: flex;
  align-items: flex-end;
}
</style>