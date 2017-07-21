<template lang="pug">
  .tutoriais
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
        .page-title Tutoriais
        q-btn(
          rounded small
          @click="addInteracao()"
          color="secondary"
        )
          q-icon(name="add_circle")
          span &nbsp;Novo tutorial
      
      // Cards de interações
      .column
        q-card.card-interacao(v-for="tutorial in [1,2,3,4,5]")
          q-card-title
            strong Como pagar as multas da biblioteca
            span Enviado por Fábio Diniz
            span 7º período de Sistemas de Informação
          q-card-main
            | Veja em detalhes como gerar a guia de recolhimento 
            | e resolver suas pendências com a biblioteca.
            .row(style="margin: 10px 0")
              q-btn(
                rounded small
                style="width: 100%"
                @click="showTutorial(tutorial)"
                color="secondary"
              )
                q-icon(name="add_circle")
                span &nbsp;Ver detalhes

    // Modal de visualização dos tutoriais
    q-modal(
      maximized
      :content-css="{padding: '30px', background: '#eceff1'}"
      ref="modalTutorial"
    )
      // Stepper
      strong.block Como pagar as multas da biblioteca
      span.block Enviado por Fábio Diniz

      q-stepper(
        vertical
        color="primary"
        style="margin-top: 20px; background: #FFF"
        ref="stepperTutorial"
      )
        q-step(
          default
          v-for="i in [1,2,3,4,5,6]"
          :title="'Passo ' + i"
          subtitle="Subtítulo"
        ) Aqui vem a descrição de cada etapa do tutorial.
          q-stepper-navigation
            q-btn(
              flat round
              color="secondary"
              icon="arrow_upward"
              @click="$refs.stepperTutorial.previous()"
            )
            q-btn(
              flat round
              color="secondary"
              icon="arrow_downward"
              @click="$refs.stepperTutorial.next()"
            )

      // Fechar modal
      .row.justify-center.full-width
        q-btn(
          color="primary"
          style="margin-top: 20px"
          @click="$refs.modalTutorial.close()"
        ) 
          q-icon(name="clear")
          span &nbsp;Fechar tutorial
</template>

<script>
import {
  QBtn,
  QIcon,
  QCard,
  QCardTitle,
  QCardMain,
  QStepper,
  QStep,
  QStepperNavigation,
  QModal,
  Dialog,
  Toast
} from 'quasar'

export default {
  components: {
    QBtn,
    QIcon,
    QCard,
    QCardTitle,
    QCardMain,
    QStepper,
    QStep,
    QStepperNavigation,
    QModal
  },
  data () {
    return {}
  },
  methods: {
    addInteracao () {
      Dialog.create({
        title: 'Novo tutorial',
        message: 'Crie seu próprio tutorial e tire as dúvidas de outros estudantes.',
        form: {
          tutorial: {
            type: 'textarea',
            label: 'Digite aqui seu tutorial'
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
    },
    showTutorial (tutorial) {
      this.$refs.modalTutorial.open()
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~variables'

.tutoriais
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
          font-size 17px
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
