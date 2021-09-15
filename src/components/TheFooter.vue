<template functional>
  <footer class="footer">
    <span class="footer__logo">
      <g-image
        src="/images/AIMV-logo-white.png"
        alt="AIMV logo"
        class="aimv-logo mt-4"
      />
      <!-- <p class="text-center">Built with &hearts; by Jack Lyons.</p> -->
    </span>

    <a class="built-by" href="https://www.jacklyons.me" target="_blank">
      Built by Jack
      <g-image
        src="tinyurl.com/e9aytpss"
        alt="A photo of Jack"
        class="jack-avatar"
      />
    </a>
  </footer>
</template>

<style lang="scss">
.footer {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0; // calc(var(--space) / 2);
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
    position: absolute;
    bottom: 2rem;
  }
}

.footer {
  @media screen and (min-width: 769px) {
    min-height: 700px;
  }

  // Match the outer page bg color
  @media screen and (min-width: 860px) {
    background-image: linear-gradient(
        to top,
        rgba(255, 153, 153, 0) 0%,
        rgba(255, 153, 153, 0) 75%,
        #0d2538
      ),
      var(--footer-bg);
  }

  .built-by {
    position: fixed;
    bottom: 0;
    left: 0;
    background: snow;
    color: #444444;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 0.5rem;
    font-size: 0.75rem;
    font-weight: bold;
    z-index: 100;
    border-radius: 2px;
    cursor: pointer;
    text-decoration: none;

    &:hover {
      background: darkslategrey;
      color: white;
    }

    .jack-avatar {
      max-width: 40px;
      border-radius: 50%;
      padding: 0.25rem;
    }

    @media screen and (max-width: 400px) {
      font-size: 0.5rem;

      .jack-avatar {
        max-width: 30px;
        padding: 0.25rem;
      }
    }
  }
}

// Light mode fade in
body[data-theme="light"] {
  .footer {
    background-image: linear-gradient(to top, rgba(255, 153, 153, 0) 75%, #fff),
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
