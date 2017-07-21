<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <router-view />
  </div>
</template>

<script>
/*
 * Root component
 */
export default {}
</script>

<style lang="stylus">
// QCard
.q-card
  border-radius 4px

// QBtn
.q-btn
  font-family 'Patrick Hand SC' !important
  font-weight 900
  font-size 18px
  padding 10px 25px
</style>
