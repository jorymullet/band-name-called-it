<script>
import ProToast from '$common/ProToast'
import Loading from '$common/Loading'
import ModalsMain from '$modals/Main'
import { UncoolAdmin } from 'uncool' // <--- Import at the top of the javascript
export default {
  name: 'App',
  components: {
    'pro-toast': ProToast,
    'loading': Loading,
    'modals-main': ModalsMain,
    'uncool-admin': UncoolAdmin, // <--- declare the component
  },
  methods: {
    getEntities (uid) {
      return uid
    },
  },
}
</script>


<template lang='pug'>
  #app
    uncool-admin
    modals-main
    router-view
    pro-toast
    loading
</template>

<style lang="sass">
  @import '$vars'
  body
    background-color: $nh-yellow
    margin: 0
    font-family: $font-1
  #app
    position: relative
</style>
