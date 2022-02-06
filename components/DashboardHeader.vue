<template>
  <header>
    <div class="main-header">
      <div class="logo-ctn">
        <img class="logo-img" src="@/assets/images/svgs/Logomark.svg" alt="">
        <div class="logo-text">
          Untitled UI
        </div>
      </div>
      <nav>
        <nuxt-link class="nav-item" to="/">
          Home
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Dashboard
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Projects
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Tasks
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Reporting
        </nuxt-link>
        <nuxt-link class="nav-item" to="/">
          Users
        </nuxt-link>
      </nav>
    </div>
    <div class="sub-header">
      yo
    </div>
  </header>
</template>

<style scoped>
.main-header,
.sub-header,
.logo-ctn,
nav {
  display: flex;
  align-items: center;
}

.main-header {
  height: 72px;
}

.sub-header {
  height: 65px;
  padding: 5px 5vw;
}

.main-header,
.sub-header {
  border-bottom: 1px solid #EAECF0;
  padding: 5px 5vw;
  gap: 20px;
}

.logo-ctn {
  gap: 5px;
}

.logo-ctn .logo-text {
  color: var(--gray-dark);
  /* font-weight: 900; */
}

nav {
  gap: 5px;
}

.nav-item {
  padding: 8px 12px;
  color: var(--gray-light);
  background: var(--gray-lighter);
  border-radius: 6px;
}
</style>