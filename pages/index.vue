<template>

  <div>
    <h1>Blog Posts</h1>

      <div v-for="post of posts" :key="post.slug">
        <NuxtLink :to="{ name: 'blog', params : { slug : post.slug }}">
          <div>
            <h2>{{ post.title }}</h2>
            <p>{{ post.description }}</p>
          </div>
        </NuxtLink>
     </div>
  </div>
</template>



<script>
  export default {
    async asyncData({ $content, params }) {
      const posts = await $content('blog')
        .only(['title', 'description', 'slug'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        posts
      }
    }
  }
</script>

