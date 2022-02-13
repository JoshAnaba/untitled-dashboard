<template>
  <div class="dashboard-ctn">
    <div class="top">
      <div class="lhs">
        <h2>Welcome back, Olivia</h2>
        <p>Track, manage and forecast your customers and orders.</p>
      </div>
      <div class="rhs">
        <button class="default-input">
          <img src="/images/svgs/import.svg" alt="" />
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
          <div class="filter-items">
            <button class="default-input">
              <span>All time</span>
              <span class="material-icons-outlined"> close </span>
            </button>
            <button class="default-input">
              <span>US, AU, +4</span>
              <span class="material-icons-outlined"> close </span>
            </button>
          </div>
          <div class="filters">
            <button class="default-input">
              <span class="material-icons-outlined"> filter_list </span>
              <span> More filters </span>
            </button>
          </div>
        </div>
        <div class="rhs">
          <div class="search-ctn">
            <label for="dashboard-search">
              <span class="material-icons-outlined"> search </span>
            </label>
            <input
              id="dashboard-search"
              type="search"
              class="default-input"
              placeholder="Search"
            />
          </div>
        </div>
      </div>
      <div class="bottom">
        <div class="table-container come-down">
          <table>
            <tr class="table-header">
              <td class="td-1">
                <div class="th-content">
                  <CustomCheckbox
                    :checked="allChecked"
                    :header="true"
                    @toggle-check="checkAll()"
                  />
                </div>
              </td>
              <td class="td-4">
                <div class="th-content">
                  <span> Company </span>
                  <span class="material-icons-outlined"> arrow_downward </span>
                </div>
              </td>
              <td class="td-3">
                <div class="th-content">License use</div>
              </td>
              <td class="td-3 hide-on-mobile-800">
                <div class="th-content">Status</div>
              </td>
              <td class="td-4 hide-on-mobile-800">
                <div class="th-content">Users</div>
              </td>
              <td class="td-5 hide-on-mobile-800">
                <div class="th-content">About</div>
              </td>
              <td class="td-2 hide-on-mobile-800" />
            </tr>
            <tbody>
              <tr v-for="(data, index) in companies" :key="index">
                <td class="td-1">
                  <div class="td-content">
                    <CustomCheckbox
                      :checked="data.checked"
                      @toggle-check="data.checked = !data.checked"
                    />
                  </div>
                </td>
                <td class="td-4">
                  <div class="td-content">
                    <div class="lhs">
                      <img
                        :src="
                          require(`@/assets/images/pngs/${data.company.name.toLowerCase()}.png`)
                        "
                        alt=""
                      />
                    </div>
                    <div class="rhs td-column">
                      <span>
                        {{ data.company.name }}
                      </span>
                      <span>
                        {{ data.company.site }}
                      </span>
                    </div>
                  </div>
                </td>
                <td class="td-3">
                  <div class="td-content">
                    <ProgressBar
                      :overview="5"
                      :current-progress="data.license_use"
                    />
                  </div>
                </td>
                <td class="td-3 hide-on-mobile-800">
                  <div :class="`td-content ${data.status}`">
                    {{ data.status }}
                  </div>
                </td>
                <td class="td-4 hide-on-mobile-800">
                  <div class="td-content">
                    <ImageRow :users="data.users" />
                  </div>
                </td>
                <td class="td-5 hide-on-mobile-800">
                  <div class="td-content">
                    <div class="td-column">
                      <span>
                        {{ data.about.title }}
                      </span>
                      <span>
                        {{ data.about.body }}
                      </span>
                    </div>
                  </div>
                </td>
                <td class="td-2 icon-space hide-on-mobile-800">
                  <div class="td-content">
                    <img src="/images/svgs/delete.svg" alt="" />
                    <img src="/images/svgs/edit.svg" alt="" />
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
          <div class="table-footer">
            <div class="lhs">
              <button
                class="default-input"
                @click="currentPage > 1 ? currentPage-- : null"
              >
                Previous
              </button>
              <button
                class="default-input"
                @click="currentPage < totalPages ? currentPage++ : null"
              >
                Next
              </button>
            </div>
            <div class="rhs">Page {{ currentPage }} of {{ totalPages }}</div>
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
      allChecked: false,
      currentPage: 1,
      totalPages: 10,
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
      companies: [
        {
          company: {
            name: 'Catalog',
            site: 'catalogapp.io',
          },
          checked: false,
          license_use: 1,
          status: 'customer',
          users: 5,
          about: {
            title: 'Content curating app',
            body: 'Brings all your news into one place',
          },
        },
        {
          company: {
            name: 'Circooles',
            site: 'getcircooles.com',
          },
          checked: false,
          license_use: 3,
          status: 'churned',
          users: 4,
          about: {
            title: 'Content curating app',
            body: 'Brings all your news into one place',
          },
        },
        {
          company: {
            name: 'Hourglass',
            site: 'hourglass.app',
          },
          checked: false,
          license_use: 4,
          status: 'customer',
          users: 5,
          about: {
            title: 'Productivity app',
            body: 'Time management and productivity',
          },
        },
        {
          company: {
            name: 'Command+R',
            site: 'cmdr.ai',
          },
          checked: false,
          license_use: 1,
          status: 'customer',
          users: 10,
          about: {
            title: 'Data prediction',
            body: 'AI and machine learning data',
          },
        },
        {
          company: {
            name: 'Layers',
            site: 'getlayers.io',
          },
          checked: false,
          license_use: 2,
          status: 'churned',
          users: 3,
          about: {
            title: 'Web app integrations',
            body: 'Connect web apps seamlessly',
          },
        },
        {
          company: {
            name: 'Quotient',
            site: 'quotient.co',
          },
          checked: false,
          license_use: 4,
          status: 'customer',
          users: 6,
          about: {
            title: 'Sales CRM',
            body: 'Web-based sales doc management',
          },
        },
        {
          company: {
            name: 'sisyphus',
            site: 'sisyphus.com',
          },
          checked: false,
          license_use: 3,
          status: 'customer',
          users: 9,
          about: {
            title: 'Automation and workflow',
            body: 'Time tracking, invoicing and expenses',
          },
        },
      ],
    }
  },
  methods: {
    checkAll() {
      this.allChecked = !this.allChecked
      if (this.allChecked) {
        this.companies = this.companies.map((c) => {
          c.checked = true
          return c
        })
      } else {
        this.companies = this.companies.map((c) => {
          c.checked = false
          return c
        })
      }
    },
  },
}
</script>

<style scoped>
.dashboard-ctn,
.dashboard-ctn > .top,
.dashboard-ctn > .top .default-input,
.dashboard-ctn > .top .rhs,
.dashboard-ctn > .middle,
.dashboard-ctn > .bottom,
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
  flex-wrap: wrap;
  gap: 20px;
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
  flex-wrap: wrap;
}

.dashboard-ctn > .bottom {
  flex-direction: column;
  gap: 25px;
}

.dashboard-ctn > .bottom .top {
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 20px;
}

.dashboard-ctn > .bottom .filter-items {
  display: flex;
  gap: 10px;
}

.dashboard-ctn > .bottom .top .lhs {
  gap: 10px;
  flex-wrap: wrap-reverse;
}

.dashboard-ctn > .top .lhs p {
  color: var(--gray-light);
}

.dashboard-ctn > .bottom .top .lhs > *,
.dashboard-ctn > .bottom .top .lhs > .filter-items > * {
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
  background: var(--purple-lightest);
  font-weight: 500;
  box-shadow: 0px 1px 2px rgba(16, 24, 40, 0.05);
  gap: 5px;
}

.dashboard-ctn > .bottom .top .lhs button:not(.filters button) span {
  color: var(--primary-purple);
}

.dashboard-ctn > .bottom .top .filters {
  border: 1px solid #d0d5dd;
  box-shadow: 0px 1px 2px rgba(16, 24, 40, 0.05);
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

.table-container {
  box-shadow: 0px 4px 8px -2px rgba(16, 24, 40, 0.1),
    0px 2px 4px -2px rgba(16, 24, 40, 0.06);
  border: 1px solid var(--border-one);
  border-radius: 8px;
  overflow-x: auto;
}

table {
  width: 100%;
  border-radius: 10px;
  border-spacing: 0;
}

td {
  padding: 0 10px;
}

tr {
  height: 72px;
}

.table-header {
  height: 44px;
}

.table-footer {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  height: 72px;
  padding: 0 10px;
}

.table-footer .lhs {
  display: flex;
  gap: 10px;
}

.table-footer .lhs button {
  border: 1px solid var(--border-one);
  border-radius: 6px;
  padding: 7px 10px;
}

table tr:last-child {
  border-collapse: separate !important;
  background: transparent;
  border-radius: 0px 0px 20px 20px;
}
table tbody tr:nth-child(odd) {
  background: var(--gray-lighter);
}
table tbody tr:nth-child(even) {
  background: #fff;
}

.icon-space div {
  gap: 20px;
}

.icon-space div span {
  cursor: pointer;
}

.td-content,
.th-content {
  display: flex;
  align-items: center;
  gap: 8px;
  height: 100%;
}

.td-content span:not(.icon-space span) {
  font-size: 14px;
}

.td-content img {
  cursor: pointer;
}

.td-content div {
  height: 100%;
}

.td-content img {
  height: 100%;
}

.th-content {
  font-weight: 400;
  color: var(--gray-light);
}

.th-content span {
  font-weight: 400;
  color: var(--gray-light);
}

.th-content:first-child span.material-icons-outlined {
  font-size: 18px;
}

.td-column {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.td-column span:first-child {
  color: var(--gray-darker);
  font-weight: 400;
}

.td-1 {
  width: calc(100% / 22);
}
.td-2 {
  width: calc(100% / 22 * 2);
}
.td-3 {
  width: calc(100% / 22 * 3);
}
.td-4 {
  width: calc(100% / 22 * 4);
}
.td-5 {
  width: calc(100% / 22 * 5);
}

.customer {
  background: #ecfdf3;
  color: var(--success);
  border-radius: 20px;
  width: 80px;
  font-size: 13px;
  padding: 3px 10px;
  display: flex;
  justify-content: center;
}

.churned {
  background: #f2f4f7;
  color: var(--gray-dark);
  border-radius: 20px;
  width: 80px;
  font-size: 13px;
  padding: 3px 10px;
  display: flex;
  justify-content: center;
}

@media screen and (max-width: 800px) {
.dashboard-ctn > .top {
  animation: slide-in-from-left .8s forwards;
  -webkit-animation: slide-in-from-left .6s forwards;
}

  .hide-on-mobile-800 {
    display: none;
  }

  .dashboard-ctn > .bottom .top {
    width: 80%;
  }

  .dashboard-ctn > .bottom .top > * {
    min-width: 80%;
  }

  .dashboard-ctn > .bottom .top .lhs .filters {
    width: 100%;
    justify-content: center;
  }
}

@media screen and (max-width: 500px) {
  .dashboard-ctn > .bottom .top {
    flex-direction: column-reverse;
    width: 100%;
  }

  .dashboard-ctn > .bottom .top > * {
    width: 100%;
  }

  .dashboard-ctn > .bottom .top .lhs > .filter-items > * {
    border-radius: 10px;
    padding: 3px 5px;
    height: 25px;
  }

  .dashboard-ctn > .bottom .top .lhs > .filter-items span {
    font-size: 14px;
  }

  .search-ctn {
    min-width: 100%;
  }

  .td-1 {
    width: calc(100% / 8);
  }
  .td-2 {
    width: calc(100% / 8 * 2);
  }
  .td-3 {
    width: calc(100% / 8 * 3);
  }
  .td-4 {
    width: calc(100% / 8 * 4);
  }
  .td-5 {
    width: calc(100% / 8 * 5);
  }
}
</style>
