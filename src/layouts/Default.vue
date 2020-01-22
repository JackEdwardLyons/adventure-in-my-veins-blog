<template>
  <section id="app">
    <main class="main">
      <slot />
    </main>

    <div class="overlap-on-footer">
      <!-- <h2 class="text-center type--raleway px-2">Follow Adventure In My Veins on Instagram 👇</h2> -->
      <!-- <instagram-feed /> -->
    </div>

    <the-footer />
  </section>
</template>

<script>
import InstagramFeed from "~/components/InstagramFeed";
import TheFooter from "~/components/TheFooter";
import TheHeader from "~/components/TheHeader";
export default {
  props: {
    showLogo: { default: true }
  },
  components: {
    InstagramFeed,
    TheFooter,
    TheHeader
  }
};
</script>

<style lang="scss">
.header {
  background-color: var(--bg-color);
  opacity: .7;
  position: sticky;
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
    opacity: 1;
    background-color: transparent;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  position: relative;
}

.overlap-on-footer {
  position: relative;
  padding-top: 5rem;
  z-index: 100;
  background: var(--bg-content-color);

  @media screen and (min-width: 769px) {
    background: var(--bg-color);
  }
}
</style>
