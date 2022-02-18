<template>
  <article>
    <h1>{{ cont.title }}</h1>
    <p>Postado em {{ formatDate(cont.createdAt) }}</p>
    <nuxt-content :document="cont" />
  </article>
</template>


<script>
export default {
  async asyncData({ $content, params }) {
    const cont = await $content("blog", params.slug).fetch();

    return { cont };
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('pt', options)
    }
  },
  head(){
    return { title : this.cont.title + " | site"}
  }
};
</script>
