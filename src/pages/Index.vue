<template>
  <Layout :show-logo="false">
    <full-height-grid :posts="featuredPosts" />
    <!-- About the blog -->
    <about-the-blog />

    <!-- More posts with tags -->
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
import FullHeightGrid from "~/components/FullHeightGrid.vue";
import AboutTheBlog from '~/components/AboutTheBlog.vue';

export default {
  components: {
    FullHeightGrid,
    AboutTheBlog
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
