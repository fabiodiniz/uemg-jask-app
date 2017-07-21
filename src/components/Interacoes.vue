<template lang="pug">
  .interacoes
    // Barra superior
    header.row.justify-center
      img.logo(src="~statics/logo-2.svg")
      q-btn.absolute-left(
        flat round
        @click="$router.go(-1)"
        color="white"
        icon="arrow_back"
        style="margin: 10px"
      )
      q-btn.absolute-right(
        flat round
        @click="$router.push('login')"
        color="white"
        icon="power_settings_new"
        style="margin: 10px"
      )
    
    // Conteúdo
    .items-list.column.items-center
      .row.justify-between.full-width(style="margin-bottom: 10px")
        .page-title Interações
        q-btn(
          rounded small
          @click="addInteracao()"
          color="secondary"
        )
          q-icon(name="add_circle")
          span &nbsp;Nova interação
      
      // Cards de interações
      .column
        q-card.card-interacao.animate-scale(v-for="i in [1,2,3,4,5]")
          q-card-title
            strong Fábio Diniz
            span 7º período de Sistemas de Informação
          q-card-main
            | Secondary line text Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam massa quam.
</template>

<script>
import {
  QBtn,
  QIcon,
  QCard,
  QCardTitle,
  QCardMain,
  Dialog,
  Toast
} from 'quasar'

export default {
  components: {
    QBtn,
    QIcon,
    QCard,
    QCardTitle,
    QCardMain
  },
  data () {
    return {}
  },
  methods: {
    addInteracao () {
      Dialog.create({
        title: 'Nova interação',
        message: `Digite sua mensagem para a comunidade acadêmica.
                  Utilize para tirar dúvidas, iniciar debates ou informar algo.`,
        form: {
          newInteracao: {
            type: 'textarea',
            rows: '7',
            label: 'Digite aqui sua interação'
          }
        },
        buttons: [
          'Cancelar',
          {
            label: 'Publicar',
            handler (data) {
              Toast.create('Returned ' + JSON.stringify(data))
            }
          }
        ]
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~variables'

.interacoes
  background #eceff1
  min-height 100vh

  > header
    background $primary
    height 80px

    > .logo
      width 130px

  > .items-list
    padding 15px

    .page-title
      font-family 'Patrick Hand SC'
      font-size 28px
      color #37474f
    
    .q-btn
      font-weight 900
      font-size 14px
      padding 6px 10px

    .card-interacao
      background #FFF
      margin 8px 0

      .q-card-primary
        background #78909c
        color #FFF

      .q-card-title
        > strong
          display block
          font-size 20px
          font-weight 900
          line-height 1.2
        > span
          display block
          font-size 14px
          font-weight 300
          font-style italic
          line-height 1.71

      .q-card-main
        padding 10px 15px
        font-size 14px
        line-height 1.43
</style>
