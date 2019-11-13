<script>
import ProInput from '$common/ProInput'
export default {
  name: 'PublicHome',
  components: {
    'pro-input': ProInput,
  },
  data () {
    return {
      form: {
        email: '',
        password: '',
      },
      formOptions: {
        email: {
          errorIf: (val) => this.$regex.is(val).a('email') ? '' : 'Enter valid email',
          title: 'Email',
          onEnter: this.login,
        },
        password: {
          errorIf: () => '',
          title: 'Password',
          type: 'password',
          onEnter: this.login,
        },
      },
    }
  },
  methods: {
    async login () {
      this.$showLoading()
      let loginRes
      try {
        loginRes = await this.$auth.signInWithEmailAndPassword(this.form.email, this.form.password)
      } catch (err) {
        this.$hideLoading()
        return this.$toast(err.message)
      }
      loginRes
    },
  },
}
</script>

<template lang="pug">
  .public-home-main
    .public-home-container
      .content
        .header.font-1-thin What band name 
          span.bold.font-1-bold you callin'?
        .uncool-things
          .picture(
            v-uncool.image='"home-pic"'
          )
          .bands-holder
            .title BANDS 
            .list(
              v-uncool='"bands-list"'
            ) a list
</template>

<style lang="sass" scoped>
  @import '$vars'
  @import '$styles/form.sass'
  .public-home-main
    .public-home-container
      .content
        display: grid
        justify-items: center
        padding-top: 80px
        width: fit-content
        margin: 0 auto
        .header
          font-size: 3em
          padding: 30px 0
          > .bold
            text-decoration: underline
        .uncool-things
          display: grid
          grid-template-columns: 400px auto
          .picture
            width: 100%
            height: 500px
          .bands-holder
            padding: 0 40px
            .title
              font-size: 2em
              font-weight: 600
              text-decoration: underline
          
</style>
