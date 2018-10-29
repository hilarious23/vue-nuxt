<template lang="pug">
  section(class="container")
    el-card(style="flex: 1")
      div(slot="header" class="clearfix")
        span ログイン
      form
        div(class="form-content")
          span ユーザーID
          el-input(placeholder="" v-model="formData.id")
        div(class="form-content")
          el-checkbox(v-model="isCreteMode") アカウントを作成する
        div(class="text-right")
          el-button(type="primary") {{ buttonText }}
</template>

<script>
export default {
  asyncData() {
    return {
      isCreateMode: false,
      formData: {
        is: ''
      }
    }
  },
  computed: {
    buttonText() {
      return this.isCreateMode ? '新規登録' : 'ログイン'
    }
  }
}
</script>

<style scoped>
.form-content {
  margin: 16px 0;
}
</style>
