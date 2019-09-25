<template>
  <Layout :title="$page.post.title">
    <g-image
      v-if="$page.post.image"
      :src="$page.post.image"
    />

    <h1 v-text="$page.post.title" />
    <div v-html="$page.post.content" />
  </Layout>
</template>

<page-query>
query Post ($id: String!) {
  post: post (id: $id) {
    title
    content
    image (width: 200, height: 100, quality: 90)
  }
}
</page-query>

<script>
import Layout from '~/layouts/Default.vue'

export default {
  components: {
    Layout
  },

  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>
