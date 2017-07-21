<template lang="pug">
  .interacoes
    header.row.justify-center
      img.logo(src="~statics/logo-2.svg")
      q-btn.absolute-left(
        flat
        round
        @click="$router.go(-1)"
        color="white"
        icon="arrow_back"
        style="margin-top: 10px; margin-right: 10px"
      )
      q-btn.absolute-right(
        flat
        round
        @click="$router.push('login')"
        color="white"
        icon="power_settings_new"
        style="margin-top: 10px; margin-right: 10px"
      )
</template>

<script>
import {
  QBtn
} from 'quasar'

export default {
  components: {
    QBtn
  },
  data () {
    return {}
  }
}
</script>

<style lang="stylus" scoped>
@import '~variables'

.interacoes
  background #eceff1
  min-height 100vh

header
  background $primary
  height 80px

  .logo
    width 130px
</style>
