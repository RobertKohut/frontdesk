<template>
  <div id="app" class="mdl-layout mdl-js-layout mdl-layout--fixed-drawer mdl-layout--fixed-header is-upgraded">
    <router-view :title="title" v-show="auth.user.authenticated"></router-view>
    <login v-show="!auth.user.authenticated" />
  </div>
</template>

<script>
window.document.app = {}
import Auth from './assets/js/auth.js'
import Login from './components/views/Login'

export default {
  name: 'app',
  components: {
    Login
  },
  data () {
    return {
      auth: Auth,
      title: 'Front Desk',
      page: ''
    }
  },
  mounted: function () {
    // Wait until the DOM has updated
    this.$nextTick(function () {
      // Once the user has authenticated, the router will automatically updates
      Auth.check()
    })
  }
}

</script>
