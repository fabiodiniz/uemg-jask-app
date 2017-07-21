<template lang="pug">
  .login.column.justify-center.items-center
    img.logo(
      src="~statics/logo-1.svg"
    )
    q-card
      q-card-title.text-center Login
      q-card-main
        form.column.items-center
          p Insira seus dados de acesso e conecte-se à comunidade acadêmica.
          q-input.full-width(
            v-model="ra"
            float-label="RA"
            color="primary"
          )
          q-input.full-width(
            v-model="senha"
            type="password"
            float-label="Senha"
            color="primary"
          )
          q-btn(
            rounded
            @click.native="$router.push('home')"
            style="margin-top: 10px"
            color="primary"
          ) 
            q-icon(name="exit_to_app")
            span &nbsp;Login
    
    router-link.link-rodape(
      to="cadastro"
    ) É novo aqui? Cadastre-se!
</template>

<script>
import {
  QCard,
  QCardTitle,
  QCardMain,
  QInput,
  QBtn,
  QIcon
} from 'quasar'

export default {
  components: {
    QCard,
    QCardTitle,
    QCardMain,
    QInput,
    QBtn,
    QIcon
  },
  data () {
    return {
      nome: '',
      ra: '',
      email: '',
      senha: ''
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~variables'

.login
  background $secondary
  min-height 100vh
  padding 20px

  > .logo
    width 130px

  > .q-card
    background #FFF
    width 100%

    > .q-card-primary
      background $primary
      color #FFF

      .q-card-title
        font-family 'Patrick Hand SC' !important
        font-size 30px !important

    > .q-card-main
      padding 0 20px 20px

      > form > p
        color #90a4ae
        font-size 16px
        text-align center
        margin 20px 0 0
        line-height 1.31
  
  > a
    color #FFF
    font-weight 900
</style>
