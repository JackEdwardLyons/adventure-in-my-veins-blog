<template>
  <section class="vh-full">
    <div class="grid-container">
      <div class="logo">
        <img class="mountain-logo" src="../../dist/images/uploads/mountains.png">
        <p class="mini-blurb">
          An adventure publication crafted for those wanderlusting, thrill seeking, 
          mountain lovers who want to build a location independent lifestyle.
        </p>
      </div>
      <g-link
        :to="post.node.path"
        v-for="(post, index) in posts"
        :key="post.node.id"
        class="flex-center grid-item post-link"
        :class="'grid-item-' + (index + 1)"
        :style="{ background: `url(${post.node.cover_image})`, backgroundSize: 'cover', }"
      >
        <div class="post-container">
          <p class="post-date">{{ simpleDate(post.node.date) }}</p>
          <h2 class="post-title">{{ post.node.title }}</h2>
          <p class="post-description">{{ truncated(post.node.description) }}</p>
        </div>
      </g-link>
    </div>
  </section>
</template>

<script>
export default {
  props: ["posts"],
  computed: {
    simpleDate () {
      return (date) => {
        // => October 2019
        return date.split(' ').slice(1).join(' ')
      }
    },
    truncated () {
      return (desc) => {
        const MAX_CHARS = 140
        return desc.length > MAX_CHARS
          ? desc.slice(0, MAX_CHARS) + ' ...'
          : desc
      }
    }
  }
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
  border: 1px solid rgba(0, 0, 0, 0.5);
}

.post-container {
  * {
    color: #fff;
    text-align: center;
  }

  .post-date {
    margin: 0;
    font-size: 90%;
  }

  .post-description {
    max-width: 80%;
    margin: 0 auto .5rem auto;
    font-size: 90%;
    color: #FCFAF5;
  }

  .post-title {
    margin: 0rem auto;
    padding: .5rem 0;
    font-size: 1.8rem;
  }
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

  .mini-blurb {
    max-width: 250px;
    color: #fff;
    font-size: 70%;
  }

  .grid-item {
    box-shadow: inset 0 0 0 1000px rgba(0, 0, 0, 0.5);
    transition: 0.8s ease;
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
