<template lang="pug">
  .home
    // Barra superior
    header.row.justify-center
      img.logo(src="~statics/logo-2.svg")
      q-btn.absolute-left(
        flat round
        @click="$router.go(-1)"
        color="white"
        icon="arrow_back"
        style="margin-top: 10px; margin-left: 10px"
      )
      q-btn.absolute-right(
        flat round
        @click="$router.push('login')"
        color="white"
        icon="power_settings_new"
        style="margin-top: 10px; margin-right: 10px"
      )
    
    // Conteúdo
    .column
      // Interações
      .info-card.row.justify-center
        .column.items-center(@click="$router.push('interacoes')")
          .title Interações
          q-card
            .row
              .imagem.row.justify-center
                img(src="~statics/interacoes-img.svg")
              .descricao Canal para debate entre discentes e docentes da universidade.

      // Tutoriais
      .info-card.-bg-green.row.justify-center
        .column.items-center(@click="$router.push('tutoriais')")
          .title Tutoriais
          q-card
            .row
              .imagem.row.justify-center
                img(src="~statics/informacoes-img.svg")
              .descricao Canal para debate entre discentes e docentes da universidade.
        
</template>

<script>
import {
  QCard,
  QBtn
} from 'quasar'

export default {
  components: {
    QCard,
    QBtn
  },
  data () {
    return {}
  }
}
</script>

<style lang="stylus" scoped>
@import '~variables'

.home
  background #eceff1
  min-height 100vh

header
  background $primary
  height 80px

  .logo
    width 130px

.info-card
  padding 10px
  cursor pointer

  .title
    color $primary
    font-family 'Patrick Hand SC' !important
    font-size 30px
    text-align center
    
  .q-card
    background #FFF

    .imagem, .descricao
      width 50%
      padding 20px

    .imagem
      > img
        max-width 100%
    
    .descricao
      background $secondary
      color #FFF
      font-family 'Patrick Hand SC' !important
      font-size 22px
      line-height 0.95
      text-align center

  &.-bg-green
    background $secondary

    .title
      color white
      
    .q-card
      .descricao
        background $primary
</style>
