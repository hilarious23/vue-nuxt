<template lang="pug">
	section(class="container")
		div
			h3 {{ userId }}
			img(:src="user.profile_image_url" width="120" alt="")
			p {{ user.description || 'No description' }}
			p
				nuxt-link(to="/")
					small
						b トップへ戻る
			h3 {{ user.id }}さんの投稿一覧
			ul
				li(v-for="item in items" :key="item.id")
					h4
						span {{ item.title }}
					div {{ item.body.slice(0, 130)}}.....
					p
						a(target="_blank" :href="item.url") {{ item.url }}
</template>

<script>
import { mapGetters } from 'vuex'

export default {
	head() {
		return {
			title: this.user.id
		}
	},
	async asyncData({ route, store, redirect }) {
		if (store.getters['users'][route.params.id]) {
			return
		}
		try {
			await store.dispatch('fetchUserInfo', { id: route.params.id })
		} catch (e) {
			consolelog("hi")
			// redirect('/')
		}
	},
	computed: {
		user() {
			return this.users[this.$route.params.id]
		},
		items() {
			return this.userItems[this.$route.params.id] || []
		},
		...mapGetters(['users', 'userItems'])
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
