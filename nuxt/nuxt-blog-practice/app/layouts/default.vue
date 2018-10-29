<template lang="pug">
  div
    TheHeader
    div(class='wrapper')
      nuxt(class="container")
</template>

<script>
import TheHeader from '~/components/TheHeader.vue'

export default {
  components: {
    TheHeader
  }
}
</script>