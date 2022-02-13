<template>
  <div class="dashboard-ctn"></div>
</template>

<script>
export default {
  name: 'ReportsPage',
  layout: 'dashboardLayout',
  created () {
    // reroute to dahsboard, as the only apps content
    this.$router.push('/dashboard')
  }
}
</script>
