<template>
  <header>
    <div class="main-header">
      <div class="lhs">
        <div class="logo-ctn">
          <img
            class="logo-img"
            src="../assets/images/svgs/Logomark.svg"
            alt=""
          />
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
      <div class="rhs">
        <button class="default-input">
          <img src="../assets/images/svgs/spark.svg" alt="">
          <span> Upgrade now </span>
        </button>
        <span class="material-icons-outlined"> settings </span>
        <span class="material-icons-outlined"> notifications </span>
        <img class="avatar" src="../assets/images/pngs/avatar.png" alt="" />
      </div>
    </div>
    <div class="sub-header">
      <nav>
        <nuxt-link class="nav-item" to="/dashboard"> Overview </nuxt-link>
        <nuxt-link class="nav-item" to="/dashboard/notifications"> Notifications </nuxt-link>
        <nuxt-link class="nav-item" to="/dashboard/analytics"> Analytics </nuxt-link>
        <nuxt-link class="nav-item" to="/dashboard/saved-reports"> Saved reports </nuxt-link>
        <nuxt-link class="nav-item" to="/dashboard/trade-history"> Trade History </nuxt-link>
        <nuxt-link class="nav-item" to="/dashboard/user-reports"> User reports </nuxt-link>
      </nav>
      <div class="search-ctn">
        <label for="search">
          <span class="material-icons-outlined"> search </span>
        </label>
        <input id="search" type="search" class="default-input" placeholder="Search" />
      </div>
    </div>
  </header>
</template>

<style scoped>
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
}

.logo-ctn .logo-text {
  color: var(--gray-darker);
  font-weight: 500;
  font-size: 18px;
}

nav {
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
</style>
