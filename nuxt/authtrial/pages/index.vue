<template lang="pug">
  div
    h2 index page
    ul
      li
        nuxt-link(to="/login") ログインページへ
      li
        nuxt-link(to="/authed-route") 認証が必要なページへ
</template>

