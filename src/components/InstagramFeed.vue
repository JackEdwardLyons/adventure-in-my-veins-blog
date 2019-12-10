<template>
  <section class="instagram-feed flex-grid thirds justify-center">
    <!-- <h1>Instagram Photos</h1> -->
    <div
      v-for="(edge) in topPosts($static.photos.edges, 4)"
      :key="edge.node.id"
      class="column instagram-post"
    >
      <g-link :href="'https://instagram.com/p/' + edge.node.shortcode" target="_blank" rel="noopener">
        <g-image
          :src="edge.node.display_url"
          :alt="'Instagram Photo: ' + edge.node.edge_media_to_caption.edges[0].node.text"
          class="photo shadow-lg"
        />
      </g-link>
    </div>
  </section>
</template>

<static-query>
query {
  photos: allInstagramPhoto {
    edges {
      node {
        id
        shortcode
        display_url
        edge_media_to_caption {
          edges {
            node {
              text
            }
          }
        }
      }
    }
  }
}
</static-query>

<script>
export default {
  computed: {
    topPosts () {
      return (posts, numPosts) => posts.slice(0, numPosts);
    }
  }
};
</script>

<style lang="scss" scoped>
.instagram-feed {
  background: var(--bg-content-color);

  @media screen and (min-width: 769px) {
    background: var(--bg-color);
  }

  .instagram-post {
    max-width: 200px;
    margin: 1rem;
    height: 100%;
  }
}
</style>