<template>
  <section class="vh-full">
    <div class="grid-container">
      <g-link
        :to="post.node.path"
        v-for="(post, index) in posts"
        :key="post.node.id"
        class="flex-center grid-item post-link"
        :class="'grid-item-' + (index + 1)"
        :style="{ background: `url(${post.node.cover_image})`, backgroundSize: 'cover', }"
      >
        <div class="post-container">
          <h4>{{ post.node.title }}</h4>
          <p class="post-date">{{ post.node.date }}</p>
        </div>
      </g-link>
    </div>
  </section>
</template>

<script>
export default {
  props: ["posts"]
};
</script>

<style lang="scss">
.vh-full {
  height: 100vh;
}

.post-link {
  cursor: pointer;
  text-decoration: none;
}

.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  border: 1px solid grey;
}

.grid-container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: repeat(3, 1fr);
  height: 100%;

  .grid-item {
    box-shadow: inset 0 0 0 1000px rgba(0, 0, 0, 0.4);
    transition: 0.8s ease;
  }

  .post-container * {
    color: #fff;
  }
}

@media screen and (min-width: 769px) {
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
