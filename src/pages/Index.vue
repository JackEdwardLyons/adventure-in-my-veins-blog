<template>
  <Layout :show-logo="false">
    <full-height-grid :posts="featuredPosts" />
    <!-- Author intro -->
    <Author :show-title="true" />

    <!-- List posts -->
    <div class="posts">
      <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node" />
    </div>
  </Layout>
</template>

<page-query>
query {
  posts: allPost(filter: { published: { eq: true }}) {
    edges {
      node {
        id
        title
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        cover_image (width: 770, height: 380, blur: 10)
        ...on Post {
        id
        title
        path
        }
        path
        tags {
          id
          title
          path
        }
      }
    }
  }
}
</page-query>

<script>
import Author from "~/components/Author.vue";
import PostCard from "~/components/PostCard.vue";
import FullHeightGrid from "~/components/FullHeightGrid.vue";

export default {
  components: {
    Author,
    PostCard,
    FullHeightGrid
  },
  metaInfo: {
    title: "Home"
  },
  computed: {
    featuredPosts() {
      return this.$page.posts.edges.slice(0, 3);
    }
  }
};
</script>
