<template>
  <Layout>
    
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <div style="width: 100%; text-align: center;">
      <g-image
        alt="Example image"
        src="~/images/luke-boom.png"
        width="200"
        style="border-radius: 50%;"
        class="shadow-2"
      />
    </div>
    
    <h1 style="text-align: center;">Blog</h1>

    <div
      style="padding: 14px; border-radius: 2px; margin-bottom: 22px;"
      class="shadow-1"
      v-for="edge in $page.posts.edges"
      :key="edge.node.id"
    >
      <g-image
        :alt="edge.node.image_alt"
        :src="edge.node.image"
        width="100%"
        style="border-radius: 50%;"
        class="shadow-2"
      />
      <h2>{{ edge.node.title }}</h2>
      <div v-text="edge.node.excerpt" />
    </div>
   

  </Layout>
</template>

<page-query>
query Posts {
	posts: allPost {
    edges {
      node { 
        id
        title
        excerpt
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}

.shadow-1 {
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
  background: white;
}

.shadow-2 {
  box-shadow: 0 2px 6px rgba(0,0,0,0.24), 0 1px 2px rgba(0,0,0,0.48);
  background: white;
}
</style>
