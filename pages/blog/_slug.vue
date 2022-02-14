<template>
  <article>
    <nuxt-content :document="cont" />
  </article>
</template>


<script>
  export default {
    async asyncData({ $content, params }) {
      const cont = await $content('blog', params.slug).fetch()

      return { cont }
    }
  }
</script>
