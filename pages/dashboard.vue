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
        <table>
        <tr class="table-header">
          <td>
            <CustomCheckbox :checked="allChecked" @toggle-check="checkAll()" />
          </td>
          <td class="flexed-td">
            <span>
              Company
            </span>
            <span class="material-icons-outlined">
              arrow_downward
            </span>
          </td>
          <td class="more-space">
            License use
          </td>
          <td>Status</td>
          <td class="more-space">
            Users
          </td>
          <td class="more-space">
            About
          </td>
          <td class="icon-btn"></td>
        </tr>
        <tbody
          v-for="(data, index) in companies"
          :key="index"
        >
          <tr>
            <td>
              <CustomCheckbox :checked="data.checked" @toggle-check="data.checked = !data.checked" />
            </td>
            <td class="flexed-td column-td">
              <span>
                {{ data.company.name }}
              </span>
              <span>
                {{ data.company.site }}
              </span>
            </td>
            <td>
              <!-- {{ data.license_use }} -->
              <ProgressBar :overview="5" :current-progress="data.license_use" />
            </td>
            <td :class="data.status">
              <div>{{data.status}}</div>
            </td>
            <td>
              <ImageRow />
            </td>
            <td class="flexed-td column-td">
              <span>
                {{data.about.title}}
              </span>
              <span>
                {{data.about.body}}
              </span>
            </td>
            <td class="icon-btn">
            <span class="material-icons-outlined">
              delete
            </span>
            <span class="material-icons-outlined">
              edit
            </span>
          </td>
          </tr>
        </tbody>
      </table>
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
            site: 'catalogapp.io'
          },
          checked: true,
          license_use: 1,
          status: 'customer',
          users: 10,
          about: {
            title: 'Content curating app',
            body: 'Brings all your news into one place'
          }
        },
        {
          company: {
            name: 'Circooles',
            site: 'getcircooles.com'
          },
          checked: false,
          license_use: 3,
          status: 'churned',
          users: 10,
          about: {
            title: 'Content curating app',
            body: 'Brings all your news into one place'
          }
        },
        {
          company: {
            name: 'Hourglass',
            site: 'hourglass.app'
          },
          checked: false,
          license_use: 4,
          status: 'customer',
          users: 10,
          about: {
            title: 'Productivity app',
            body: 'Time management and productivity'
          }
        },
        {
          company: {
            name: 'Command+R',
            site: 'cmdr.ai'
          },
          checked: true,
          license_use: 1,
          status: 'customer',
          users: 10,
          about: {
            title: 'Data prediction',
            body: 'AI and machine learning data'
          }
        },
        {
          company: {
            name: 'Layers',
            site: 'getlayers.io'
          },
          checked: true,
          license_use: 2,
          status: 'churned',
          users: 10,
          about: {
            title: 'Web app integrations',
            body: 'Connect web apps seamlessly'
          }
        },
        {
          company: {
            name: 'Quotient',
            site: 'quotient.co'
          },
          checked: false,
          license_use: 4,
          status: 'customer',
          users: 10,
          about: {
            title: 'Sales CRM',
            body: 'Web-based sales doc management'
          }
        },
        {
          company: {
            name: 'sisyphus',
            site: 'sisyphus.com'
          },
          checked: true,
          license_use: 3,
          status: 'customer',
          users: 9,
          about: {
            title: 'Automation and workflow',
            body: 'Time tracking, invoicing and expenses'
          }
        },
      ]
    }
  },
  methods: {
    checkAll () {
    this.allChecked = !this.allChecked
      if (this.allChecked) {
        this.companies = this.companies.map(c => {
          c.checked = true
          return c
        })
      } else {
        this.companies = this.companies.map(c => {
          c.checked = false
          return c
        })
      }
    }
  }
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
  gap: 25px;
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

table {
  width: 100%;
}

tr {
  height: 72px;
}
/* tr { */
  /* display: flex; */
/* } */

td {
  /* display: flex;
  align-items: center; */
  padding: 20px 0;
}

.flexed-td {
  display: flex;
}

.column-td {
  flex-direction: column;
}

.customer div {
  background: #ECFDF3;
  color: #027A48;
  border-radius: 20px;
  width: 80px;
  font-size: 13px;
  padding: 3px 10px;
  display: flex;
  justify-content: center;
}

.churned div {
  background: #F2F4F7;
  color: var(--gray-dark);
  border-radius: 20px;
  width: 80px;
  font-size: 13px;
  padding: 3px 10px;
  display: flex;
  justify-content: center;
}
</style>
