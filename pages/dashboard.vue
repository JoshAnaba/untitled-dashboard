<template>
  <div class="dashboard-ctn">
    <div class="top">
      <div class="lhs">
        <h2>Welcome back, Olivia</h2>
        <p>Track, manage and forecast your customers and orders.</p>
      </div>
      <div class="rhs">
        <button class="default-input">
          <span class="material-icons-outlined"> cloud_upload </span>
          <span>Import</span>
        </button>
        <button class="default-input">
          <span class="material-icons-outlined"> add </span>
          <span>Add</span>
        </button>
      </div>
    </div>
    <div class="middle">
      <DashboardCard
        v-for="(card, index) in cards"
        :key="index"
        :details="card"
      />
    </div>
    <div class="bottom">
      <div class="top">
        <div class="lhs">
          <button class="default-input">
            <span>All time</span>
            <span class="material-icons-outlined"> close </span>
          </button>
          <button class="default-input">
            <span>US, AU, +4</span>
            <span class="material-icons-outlined"> close </span>
          </button>
          <div class="filters">
            <button class="default-input">
              <span class="material-icons-outlined"> filter_list </span>
              <span> More filters </span>
            </button>
          </div>
        </div>
        <div class="rhs">
          <div class="search-ctn">
            <label for="search">
              <span class="material-icons-outlined"> search </span>
            </label>
            <input
              id="search"
              type="search"
              class="default-input"
              placeholder="Search"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DashboardPage',
  layout: 'dashboardLayout',
  data() {
    return {
      cards: [
        {
          name: 'Total customers',
          metric: '2,420',
          rise: true,
          value: '40',
        },
        {
          name: 'Members',
          metric: '1,210',
          rise: false,
          value: '10',
        },
        {
          name: 'Active now',
          metric: '316',
          rise: true,
          value: '20',
        },
      ],
    }
  },
}
</script>

<style scoped>
.dashboard-ctn,
.dashboard-ctn > .top,
.dashboard-ctn > .top .default-input,
.dashboard-ctn > .top .rhs,
.dashboard-ctn > .middle,
.dashboard-ctn > .bottom .top,
.dashboard-ctn > .bottom .top .lhs {
  display: flex;
}

.dashboard-ctn {
  flex-direction: column;
  gap: 30px;
}
.dashboard-ctn > .top {
  justify-content: space-between;
}

.dashboard-ctn > .top .default-input {
  align-items: center;
  gap: 5px;
  border-radius: 8px;
  height: 40px;
  padding: 5px 20px;
}

.dashboard-ctn > .top .default-input:first-child {
  border: 1px solid #d0d5dd;
}

.dashboard-ctn > .top .default-input:last-child {
  background: var(--primary-purple);
}

.dashboard-ctn > .top .default-input:last-child span {
  color: #fff;
}

.dashboard-ctn > .top .rhs {
  gap: 20px;
}

.dashboard-ctn > .middle {
  justify-content: space-between;
  gap: 15px;
}

.dashboard-ctn > .bottom {
  flex-direction: column;
}

.dashboard-ctn > .bottom .top {
  justify-content: space-between;
}

.dashboard-ctn > .bottom .top .lhs {
  gap: 10px;
}

.dashboard-ctn > .bottom .top .lhs > * {
  display: flex;
  align-items: center;
  border-radius: 6px;
  height: 40px;
  padding: 7px 10px;
}

.dashboard-ctn > .bottom .top .lhs .filters button {
  display: flex;
  align-items: center;
  gap: 5px;
}

.dashboard-ctn > .bottom .top .lhs button:not(.filters button) {
  background: #f9f5ff;
  box-shadow: 0px 1px 2px rgba(16, 24, 40, 0.05);
  gap: 5px;
}

.dashboard-ctn > .bottom .top .lhs button:not(.filters button) span {
  color: var(--primary-purple);
}

.dashboard-ctn > .bottom .top .filters {
  border: 1px solid #d0d5dd;
}

.search-ctn,
.search-ctn label {
  display: flex;
  align-items: center;
}

.search-ctn {
  border-radius: 8px;
  border: 1px solid #d0d5dd;
  color: var(--gray-dark);
  padding: 8px 12px;
}

.search-ctn {
  gap: 5px;
  height: 47px;
  min-width: 350px;
  justify-content: space-between;
}

.search-ctn label {
  width: 10%;
  justify-content: center;
}

.search-ctn input {
  font-weight: 200;
  width: 90%;
}
</style>
