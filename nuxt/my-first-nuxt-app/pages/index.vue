<template lang="pug">
  section(class="container")
    div
      h3 Nuxt.jsのタグが付けられた投稿一覧
      ul
        li(v-for="item in items" :key="item.id")
          h4
            span {{ item.title }}
            small 
              span by
              nuxt-link(:to="`/users/${item.user.id}`") {{ item.user.id }}
          div {{ item.body.slice(0, 130) }}
          p
            a(:href="item.url") {{ item.url }}
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  async asyncData({ store }) {
    if (store.getters['items'].length) {
      return
    }
    await store.dispatch('fetchItems')
  },
  computed: {
    ...mapGetters(['items'])
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  padding: 16px;
}

h3 {
  margin: 16px 0;
  padding: 8px 0;
  border-bottom: solid 1px #e5e5e5;
}

li + li {
  margin: 16px 0;
}

p {
  margin: 8px 0;
}
</style>
