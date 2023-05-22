<template>
  <div class="dashboard-ctn" />
</template>

<script>
export default {
  name: 'IndexPage',
  layout: 'dashboardLayout',
  created () {
    // reroute to dahsboard, as the only apps content
    this.$router.push('/dashboard')
  }
}
</script>
