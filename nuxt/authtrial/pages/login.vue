<template lang="pug">
  div
    h2 ログインページ
    p
      button(type="button" @click="login") ログイン
      nuxt-link(to='/') トップページへ
</template>

<script>
import Cookies from 'universal-cookie'
export default {
  methods: {
    login() {
      const cookies =new Cookies()
      cookies.set('credential', 'true', { maxAge: 90 })
      this.$router.push('/')
    }
  }
}
</script>
