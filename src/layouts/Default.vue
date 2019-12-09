<template>
  <div id="app">
    <main class="main">
      <slot />
    </main>

    <footer class="footer">
      <span class="footer__logo">
        <g-image
          alt="AIMV logo"
          src="https://codex-themes.com/thegem/sites/travel-blog/wp-content/uploads/2019/05/35.png"
        ></g-image>
        <p class="text-center">Built with &hearts; by Jack Lyons.</p>
      </span>
    </footer>
  </div>
</template>

<script>
import Author from "~/components/Author.vue";

export default {
  props: {
    showLogo: { default: true }
  },
  components: {
    Author
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
  background-image: var(--footer-bg);
  background-size: cover;
  background-position: center;
  min-height: 600px;
  // Dark mode bg fade
  // Match the inner post bg color
  background-image: linear-gradient(
      to top,
      rgba(255, 153, 153, 0) 0%,
      rgba(255, 153, 153, 0) 75%,
      #0f2d44
    ),
    var(--footer-bg);

  &__logo {
    max-width: 250px;
    position: absolute;
    bottom: 2rem;
    color: white;
  }
}

@media screen and (min-width: 769px) {
  .footer {
    min-height: 700px;
  }
}

// Match the outer page bg color
@media screen and (min-width: 860px) {
  .footer {
    background-image: linear-gradient(
        to top,
        rgba(255, 153, 153, 0) 0%,
        rgba(255, 153, 153, 0) 75%,
        #0d2538
      ),
      var(--footer-bg);
  }
}

// Light mode fade in
body[data-theme="light"] {
  .footer {
    background-image: linear-gradient(
      to top, 
      rgba(255, 153, 153, 0) 75%, 
      #fff),
      var(--footer-bg);
  }
}

// Light mode fade in on large screens
@media screen and (min-width: 769px) {
  body[data-theme="light"] {
    .footer {
      background-image: linear-gradient(
          to top,
          rgba(255, 153, 153, 0) 75%,
          #f3f7f9
        ),
        var(--footer-bg);
    }
  }
}
</style>
