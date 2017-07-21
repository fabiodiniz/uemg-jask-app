<template lang="pug">
  .login.column.justify-center.items-center
    img.logo(
      src="~statics/logo-1.svg"
    )
    q-card
      q-card-title.text-center Login
      q-card-main.column.items-center
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
          big
          rounded
          style="margin-top: 10px"
          color="primary"
        ) Login
    
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
  QBtn
} from 'quasar'

export default {
  components: {
    QCard,
    QCardTitle,
    QCardMain,
    QInput,
    QBtn
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

<style lang="stylus">
@import '~variables'

.login
  background $secondary
  height 100vh
  padding 20px

  > .logo
    width 130px

  > .q-card
    background #FFF
    width 100%

    > .q-card-primary
      background $primary
      color #FFF

    > .q-card-main
      padding 0 20px 20px
  
  > a
    color #FFF
    font-weight 900
</style>
