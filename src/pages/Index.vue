<template>
  <Layout :show-logo="false">
    <!-- About the blog -->
    <about-the-blog />
    <!-- Featured articles -->
    <full-height-grid :posts="featuredPosts" />
    <section class="infinite-scroll-container">
      <transition-group name="fade" tag="div">
        <div key="posts">
          <!-- <full-height-grid :posts="nonFeaturedPosts" /> -->
          <flex-post-grid :posts="nonFeaturedPosts" />
        </div>
      </transition-group>
      <ClientOnly>
        <infinite-loading @infinite="infiniteHandler" spinner="spiral">
          <div slot="no-more">  </div>
          <div slot="no-results">Sorry, no posts yet 🥶</div>
        </infinite-loading>
      </ClientOnly>
    </section>
  </Layout>
</template>

<page-query>
query Blog($page: Int) {
	posts: allPost(perPage: 6, page: $page) @paginate {
		pageInfo {
			totalPages
			currentPage
		}
		edges {
			node {
				id
				title
				date (format: "D. MMMM YYYY")
				timeToRead
				description
				cover_image (width: 770, height: 380, blur: 10)
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
import FlexPostGrid from "~/components/FlexPostGrid.vue";
import FullHeightGrid from "~/components/FullHeightGrid.vue";
import AboutTheBlog from "~/components/AboutTheBlog.vue";

// FIXME: Have a query for all posts
// Have a query for paginated posts
// Keep featured posts at top
export default {
  components: {
    FlexPostGrid,
    FullHeightGrid,
    AboutTheBlog
  },
  data() {
    return {
      loadedPosts: [],
      currentPage: 1
    };
  },
  created() {
    this.loadedPosts.push(...this.$page.posts.edges);
  },
  metaInfo: {
    title: "Welcome to Adventure In My Veins",
    meta: [
        {
          name: "description",
          content: 'An adventure publication crafted for wanderlusting, thrill seeking, mountain lovers who want to build a location independent lifestyle.'
        },
        {
          property: "og:title",
          content: 'Welcome to Adventure In My Veins'
        },
        {
          property: "og:image",
          content: 'https://www.adventureinmyveins.com/images/AIMV-logo-black.png'
        },
        {
          property: 'og:image:width',
          content: '300'
        },
        {
          property: 'og:image:height',
          content: '300'
        }
      ]
  },
  methods: {
    async infiniteHandler($state) {
      if (this.currentPage + 1 > this.$page.posts.pageInfo.totalPages) {
        $state.complete();
      } else {
        const { data } = await this.$fetch(`/${this.currentPage + 1}`);
        if (data.posts.edges.length) {
          this.currentPage = data.posts.pageInfo.currentPage;
          this.loadedPosts.push(...data.posts.edges);
          $state.loaded();
        } else {
          $state.complete();
        }
      }
    }
  },
  computed: {
    featuredPosts() {
      const featuredPosts = this.loadedPosts.filter(edge => {
        return edge.node.tags.some(tag =>
          tag.title.toLowerCase().includes("featured")
        );
      });
      // to be sure we always just get the top 3 posts
      return featuredPosts.slice(0, 3);
    },
    nonFeaturedPosts() {
      const nonFeaturedPosts = this.loadedPosts.filter(edge => {
        return edge.node.tags.every(tag => {
          return !tag.title.toLowerCase().includes("featured");
        });
      });
      return nonFeaturedPosts;
    }
  },
  mounted () {
    console.log(this.$page)
  }
};
</script>
<style>
.fade-enter-active,
.fade-leave-active {
  transition: ease opacity 0.3s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.infinite-scroll-container {
  padding: .5rem 1.5rem;
}
</style>