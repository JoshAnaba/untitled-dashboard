<template>
  <div class="dashboard-layout-ctn">
    <DashboardHeader />
    <Nuxt class="main-ctn" />
  </div>
</template>

<style scoped>
.main-ctn {
  padding: 50px 8vw;
}

@media screen and (max-width: 1000px) {
  .main-ctn {
    padding: 30px 4vw;
  }
}
</style>