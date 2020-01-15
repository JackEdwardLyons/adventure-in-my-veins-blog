<template>
  <section class="flex-grid three-post-grid">
    <g-link
      :to="post.node.path"
      v-for="(post) in posts"
      :key="post.node.id"
      class="post-link column box-shadow-effect post-item"
      :style="{ background: `url(${post.node.cover_image}) repeat scroll 0% 0% / cover` }"
      :aria-label="`Click to view '${post.node.title}'`"
    >
      <single-grid-post :post="post" :max-chars="60" />
    </g-link>
  </section>
</template>

<script>
import SingleGridPost from "~/components/SingleGridPost.vue";

export default {
  props: ["posts"],
  components: {
    SingleGridPost
  }
};
</script>

<style lang="scss">
.three-post-grid {
  height: 50vh;
  padding: 0 1.5rem;
  display: flex;
  max-height: 400px;

  .post-title {
    font-size: 1.2rem;
  }
  
  .column {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 1.5rem 0 0;

    @media screen and (min-width: 768px) {
      &:nth-child(2) {
        margin: 1.5rem 0 0 1.5rem;
      }
    }

    @media screen and (min-width: 1110px) {
      &:first-child {
        margin-right: 0;
      }
      &:nth-child(2) {
        margin: 1.5rem 0 0 0;
      }
      &:last-child {
        margin: 1.5rem 0;
      }
    }

    @media screen and (min-width: 1200px) {
      &:nth-child(2) {
        margin: 1.5rem 1.5rem 0;
      }

      &:last-child {
        margin: 1.5rem 0 0;
      }
    }
  }
}
</style>