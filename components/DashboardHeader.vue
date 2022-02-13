<template>
  <header>
    <div class="main-header">
      <div class="lhs slide-in-from-left">
        <div class="logo-ctn" @click="$router.push('/')">
          <img class="logo-img" src="/images/svgs/Logomark.svg" alt="" />
          <div class="logo-text">Untitled UI</div>
        </div>
        <nav>
          <nuxt-link class="nav-item" to="/"> Home </nuxt-link>
          <nuxt-link class="nav-item" to="/dashboard"> Dashboard </nuxt-link>
          <nuxt-link class="nav-item" to="/projects"> Projects </nuxt-link>
          <nuxt-link class="nav-item" to="/tasks"> Tasks </nuxt-link>
          <nuxt-link class="nav-item" to="/reports"> Reporting </nuxt-link>
          <nuxt-link class="nav-item" to="/users"> Users </nuxt-link>
        </nav>
      </div>
      <div class="rhs slide-in-from-right">
        <button class="default-input">
          <img src="/images/svgs/spark.svg" alt="" />
          <span> Upgrade now </span>
        </button>
        <span class="material-icons-outlined"> settings </span>
        <span class="material-icons-outlined"> notifications </span>
        <img class="avatar" src="/images/pngs/avatar.png" alt="" />
      </div>
      <MenuBtn @toggle-mobile-menu="toggleMobileMenu" />
    </div>
    <div class="sub-header">
      <nav class="slide-in-from-left">
        <nuxt-link class="nav-item" to="/dashboard"> Overview </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Notifications
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Analytics
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Saved reports
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Trade History
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          User reports
        </nuxt-link>
      </nav>
      <div class="search-ctn slide-in-from-right">
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
    <div v-show="showMobileMenu" ref="nav" class="nav-mobile">
      <div class="inner">
        <div class="nav-actions-mobile">
          <nuxt-link class="nav-item" to="/">Home </nuxt-link>
          <nuxt-link class="nav-item" to="/dashboard"> Dashboard </nuxt-link>
          <nuxt-link class="nav-item" to="/projects"> Projects </nuxt-link>
          <nuxt-link class="nav-item" to="/tasks"> Tasks </nuxt-link>
          <nuxt-link class="nav-item" to="/reports"> Reporting </nuxt-link>
          <nuxt-link class="nav-item" to="/users"> Users </nuxt-link>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'DashboardHeader',
  data() {
    return {
      showMobileMenu: false,
    }
  },
  watch: {
    $route: {
      handler() {
        this.showMobileMenu = false
      },
    },
    showMobileMenu: {
      handler(val) {
        if (val) {
          this.$refs.nav.classList.add('come-down')
        }
      },
    },
  },
  methods: {
    toggleMobileMenu(boo) {
      this.showMobileMenu = boo
    },
  },
}
</script>

<style scoped>
header {
  position: relative;
}

.main-header,
.sub-header,
.logo-ctn,
nav,
.lhs,
.rhs,
.rhs .default-input,
.search-ctn,
.search-ctn label {
  display: flex;
  align-items: center;
}

.lhs {
  gap: 25px;
}

.main-header {
  height: 72px;
}

.sub-header {
  height: 65px;
}

.nuxt-link-exact-active {
  background: var(--gray-lighter);
}

.main-header,
.sub-header {
  border-bottom: 1px solid var(--border-one);
  padding: 5px 8vw;
  gap: 20px;
  justify-content: space-between;
}

.logo-ctn {
  gap: 5px;
  cursor: pointer;
}

.logo-ctn .logo-text {
  color: var(--gray-darker);
  font-weight: 500;
  font-size: 18px;
}

.main-header nav,
.sub-heder nav {
  gap: 5px;
}

.nav-item {
  padding: 8px 12px;
  color: var(--gray-dark);
  border-radius: 6px;
  font-weight: 400;
  height: 40px;
}

.rhs {
  gap: 20px;
}

.rhs .default-input {
  padding: 8px 12px;
}

.rhs .default-input,
.sub-header .search-ctn {
  border-radius: 8px;
  border: 1px solid #d0d5dd;
  color: var(--gray-dark);
  padding: 8px 12px;
}

.rhs span.material-icons-outlined {
  color: var(--gray-light);
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

.rhs .default-input {
  height: 42px;
}

.nav-mobile {
  display: none;
  border-radius: 0 0 5px 5px;
  width: 90vw;
  margin: 0 5vw;
  background: #fff;
  box-shadow: -1px 10px 10px 10px rgba(18, 94, 164, 0.08);
  z-index: 5;
  padding: 0 20px 10px 20px;
  position: absolute;
}

.nav-actions-mobile {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.nav-actions-mobile .nav-item {
  height: 50px;
  display: flex;
  align-items: center;
}

.nav-mobile .inner {
  z-index: 5;
  padding: 20px 0;
}

@media screen and (max-width: 1000px) {
  .main-header {
    padding: 3px 4vw;
    height: 64px;
  }
  .nav-mobile {
    display: block;
  }

  .sub-header,
  nav,
  .rhs {
    display: none;
  }
}
</style>
