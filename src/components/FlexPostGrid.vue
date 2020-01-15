<template>
  <section class="flex-grid flex-post-grid">
    <g-link
      :to="post.node.path"
      v-for="(post) in posts"
      :key="post.node.id"
      class="post-link column box-shadow-effect post-item m-1-2"
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
.post-item {
  min-height: 200px;
  max-height: 350px;
}
.flex-post-grid {
  // min-height: 40vh;
  // padding: 0 1.5rem;
  margin-left: -.5rem;
  margin-right: -.5rem;
  display: flex;

  .post-title {
    font-size: 1.2rem;
  }

  .column {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: .5rem;
  }
}
</style>