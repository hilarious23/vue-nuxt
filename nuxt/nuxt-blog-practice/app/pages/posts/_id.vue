<template lang="pug">
  section(class="container posts-page")
    div(style="flex: 1")
      el-card(v-if="post")
        div(slot="header" class="clearfix")
          h2 {{ post.title}}
          small by {{ post.user.id }}
        p {{ post.body }}
        p(class="text-right") {{ post.created_at | time }}
      p
        nuxt-link(to="/posts") &lt; 投稿一覧へ戻る   
</template>

<script>
import moment from '~/plugins/moment'
import { mapGetters, mapActions } from 'vuex'

export default {
  async asyncData({ store, route, error }) {
    const { id } = route.params
    if (store.getters['posts/posts'].find(p => p.id === id)) {
      return
    }
    try {
      await store.dispatch('posts/fetchPost', { id })
      if (!(store.getters['posts/posts'].find(p => p.id === this.$route.params.id))) {
        throw new Error('post not found')
      }
    } catch(e) {
      error({ statusCode: 404 })
    }
  },
  computed: {
    post() {
      return this.posts.find(p => p.id === this.$route.params.id)
    },
    ...mapGetters('posts', ['posts'])
  },
  filters: {
    time(val) {
      return moment(val).format('YYYY/MM/DD HH:mm:ss')
    }
  }
}
</script>

<style>
.post-page .el-table__row {
  cursor: pointer;
}
</style>

