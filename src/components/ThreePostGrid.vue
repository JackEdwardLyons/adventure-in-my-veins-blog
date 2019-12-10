<template>
  <section class="flex-grid reduced-size-type">
    <g-link
      :to="post.node.path"
      v-for="(post) in posts"
      :key="post.node.id"
      class="post-link column"
      :style="{ background: `url(${post.node.cover_image})`, backgroundSize: 'cover', backgroundPosition: 'center' }"
    >
      <single-grid-post :post="post" />
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
.reduced-size-type {
  min-height: 60vh;

  * {
    .post-title {
      font-size: 1.2rem;
    }
  }
}

.reduced-size-type {
  .column {
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>