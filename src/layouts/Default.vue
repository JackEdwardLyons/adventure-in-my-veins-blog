<template>
  <div id="app">
    <main class="main">
      <slot />
    </main>

    <div class="overlap-on-footer">
      <h2 class="text-center type--rock-salt">Follow AIMV on Instagram</h2>
      <instagram-feed />
    </div>

    <the-footer />
  </div>
</template>

<script>
import InstagramFeed from "~/components/InstagramFeed.vue";
import TheFooter from "~/components/TheFooter";
export default {
  props: {
    showLogo: { default: true }
  },
  components: {
    InstagramFeed,
    TheFooter
  }
};
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top: 0;
  z-index: 10;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  @media screen and (min-width: 1300px) {
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  position: relative;
}

.overlap-on-footer {
  padding-top: 3rem;
  z-index: 100;
  background: var(--bg-color);
}
</style>
