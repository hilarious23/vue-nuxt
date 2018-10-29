<template lang="pug">
  el-menu(mode="horizontal" :router="true")
    el-menu-item(index="1" style="pointer-events:none;") Nuxt Diary App
    el-menu-item(index="2" :route="{ path: '/posts' }") 投稿一覧

    no-ssr
      el-menu-item(index="4" style="float: right;" :route="{ path: '/' }")
        span Login
    el-menu-item(index="5" style="float: right;" :route="{ path: '/posts/new' }") 新規投稿
</template>
