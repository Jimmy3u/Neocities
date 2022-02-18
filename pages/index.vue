<template>
  <div>
    <h1>Blog Posts</h1>
      <div v-for="post of posts" :key="post.slug">
          <div>
          <NuxtLink :to="{ name: 'blog', params : { slug : post.slug }}">
            <h2>{{ post.title }}</h2></NuxtLink>
            <p>{{ post.description }}</p>
          </div>

     </div>
  </div>
</template>



<script>
  export default {

    async asyncData({ $content, params }) {
      const posts = await $content('blog')
        .only(['title', 'description', 'slug'])
        .sortBy('createdAt', 'desc')
        .fetch()

      return {
        posts
      }
    }
  }
</script>

