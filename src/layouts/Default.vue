<template>
  <div id="app">
    <main class="main">
      <slot />
    </main>

    <footer class="footer">
      <span class="footer__logo">
        <g-image alt="AIMV logo" src="https://codex-themes.com/thegem/sites/travel-blog/wp-content/uploads/2019/05/35.png"></g-image>
        <p class="text-center">
          Built with &hearts; by Jack Lyons.
        </p>
      </span>
    </footer>
  </div>
</template>

<script>
export default {
  props: {
    showLogo: { default: true }
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
    //Make header sticky for large screens
    // position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  // padding: 1.5vw 15px 0;
  position: relative;
}

.footer {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: calc(var(--space) / 2);
  text-align: center;
  position: relative;
  background-image: url('https://codex-themes.com/thegem/sites/travel-blog/wp-content/uploads/2019/05/34-1.jpg');
  background-size: cover;
  min-height: 1000px;

  &__logo {
    max-width: 250px;
    position: absolute;
    bottom: 2rem;
    color: white;
  }
}
</style>
