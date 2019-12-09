<template>
  <Layout :show-logo="false">
    <full-height-grid :posts="featuredPosts" />
    <!-- Author intro -->
    <Author :show-title="true" />
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
import FullHeightGrid from "~/components/FullHeightGrid.vue";

export default {
  components: {
    Author,
    FullHeightGrid
  },
  metaInfo: {
    title: "Home"
  },
  computed: {
    featuredPosts() {
      const featuredPosts = this.$page.posts.edges.filter(edge => {
        return edge.node.tags.some(tag =>
          tag.title.toLowerCase().includes("featured")
        );
      });
      // to be sure we always just get the top 3 posts
      return featuredPosts.slice(0, 3);
    }
  }
};
</script>
