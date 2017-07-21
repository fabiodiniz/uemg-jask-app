<template lang="pug">
  .interacoes
    // Barra superior
    header.row.justify-center.fixed-top
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
        q-card.card-interacao.animate-scale(v-for="interacao in interacoes")
          q-card-title
            strong {{ interacao.nome }}
            span {{ interacao.curso }}
          q-card-main
            | {{ interacao.texto }}

    // Filtros
    .row.fixed-bottom
      q-tabs.full-width(align="center" color="secondary")
        q-tab(
          default inverted
          slot="title"
          color="white"
          label="UEMG"
          name="tab-1"
          icon="message"
        )
        q-tab(
          inverted
          slot="title"
          color="white"
          count="3"
          label="Meu curso"
          name="tab-2"
          icon="message"
        )
        q-tab(
          inverted
          slot="title"
          color="white"
          count="5"
          label="Minha sala"
          name="tab-3"
          icon="message"
        )
</template>

<script>
import {
  QBtn,
  QIcon,
  QCard,
  QCardTitle,
  QTabs,
  QTab,
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
    QTabs,
    QTab,
    QCardMain
  },
  data () {
    return {
      interacoes: [{
        'nome': 'Fábio Diniz',
        'curso': '7º período de Sistemas de Informação',
        'texto': 'Vem aí o I Startup Experience! Dias 28, 29 e 30 de Julho. Traga sua ideia e venha trabalhar nela conosco :)'
      }]
    }
  },
  methods: {
    addInteracao () {
      let vue = this

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
              vue.interacoes.unshift({
                'nome': 'Fábio Diniz',
                'curso': '7º período de Sistemas de Informação',
                'texto': data.newInteracao
              })
              Toast.create.positive('Interação publicada :)')
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
  padding 90px 0 70px

  > header
    background $primary
    height 80px
    z-index 999

    > .logo
      width 130px

  > .items-list
    margin auto
    max-width 500px
    padding 15px 15px

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
