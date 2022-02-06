<template>
  <div class="dashboard-ctn">
    <div class="top">
      <div class="lhs">
        <h2>Welcome back, Olivia</h2>
        <p>Track, manage and forecast your customers and orders.</p>
      </div>
      <div class="rhs">
        <button class="default-input">
          <span class="material-icons-outlined">
            cloud_upload
          </span>
          <span>Import</span>
        </button>
        <button class="default-input">
          <span class="material-icons-outlined">
            add
          </span>
          <span>Add</span>
        </button>
      </div>
    </div>
    <div class="middle">
      <DashboardCard v-for="(card, index) in cards" :key="index" :details="card" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'DashboardPage',
  layout: 'dashboardLayout',
  data () {
    return {
      cards: [
        {
          name: 'Total customers',
          metric: '2,420',
          rise: true,
          value: '40'
        },
        {
          name: 'Members',
          metric: '1,210',
          rise: false,
          value: '10'
        },
        {
          name: 'Active now',
          metric: '316',
          rise: true,
          value: '20'
        }
      ]
    }
  }
}
</script>

<style scoped>
.dashboard-ctn {
  display: flex;
  flex-direction: column;
  gap: 30px;
}
.dashboard-ctn .top {
  display: flex;
  justify-content: space-between;
}

.top .default-input {
  display: flex;
  align-items: center;
  gap: 5px;
  border-radius: 8px;
  height: 40px;
  padding: 5px 20px;
}

.top .default-input:first-child {
  border: 1px solid #d0d5dd;
}

.top .default-input:last-child {
  background: var(--primary-purple);
}

.top .default-input:last-child span {
  color: #fff;
}

.top .rhs {
  display: flex;
  gap: 20px;
}

.middle {
  display: flex;
  justify-content: space-between;
  gap: 15px;
}
</style>
