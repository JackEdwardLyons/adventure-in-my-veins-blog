<template>
  <section class="vh-full">
    <div class="grid-container">
      <div class="logo">
        <!-- <img class="mountain-logo" src="../../dist/images/uploads/mountains.png"> -->
        <p class="mini-blurb">
          An adventure publication crafted for those wanderlusting, thrill seeking,
          mountain lovers who want to build a location independent lifestyle.
        </p>
      </div>

      <g-link
        :to="post.node.path"
        v-for="(post, index) in posts"
        :key="post.node.id"
        class="grid-item-center box-shadow-effect post-link"
        :class="'grid-item-' + (index + 1)"
        :style="{ background: `url(${post.node.cover_image})`, backgroundSize: 'cover', }"
      >
        <single-grid-post :post="post" />
      </g-link>
    </div>
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
.grid-item-center {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  border: 1px solid rgba(0, 0, 0, 0.5);
}

.grid-container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: repeat(3, 1fr);
  height: 100%;
  position: relative;

  .logo {
    position: absolute;
    top: 2rem;
    left: 2rem;
    z-index: 99999;
    display: flex;

    .mountain-logo {
      height: 50px;
      margin-top: 1rem;
      margin-right: 20px;
    }
  }
}

.mini-blurb {
  max-width: 250px;
  color: #fff;
  font-size: 80%;
  display: none;
}

@media screen and (min-width: 769px) {
  .mini-blurb {
    max-width: 250px;
    color: #fff;
    font-size: 70%;
    display: block;
  }

  .grid-container {
    display: grid;
    grid-template-columns: 50% 50%;
    width: 100%;
  }

  .grid-container {
    display: grid;
    // If the definition contains repeating parts,
    // use the repeat() notation to streamline things:
    grid-template-columns: repeat(2, 1fr);
    // The fr unit allows you to set the size of a
    // track as a fraction of the free space of
    // the grid container.
    grid-template-rows: repeat(2, 1fr);

    // Short-shorthand for grid-row-start + grid-column-start
    // + grid-row-end + grid-column-end:
    .grid-item-1 {
      grid-area: 1 / 1 / 3 / 2;
    }
    .grid-item-2 {
      grid-area: 1 / 2 / 2 / 3;
    }
    .grid-item-3 {
      grid-area: 2 / 2 / 3 / 3;
    }
  }
}
</style>
