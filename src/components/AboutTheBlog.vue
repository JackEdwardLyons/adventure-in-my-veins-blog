<template>
  <section class="about-the-blog flex-grid">
    <div class="column text-center" style="width: 90%; max-width: 700px; margin: 0 auto;">
      <h2 class="type--rock-salt">Adventure In My Veins ...</h2>
      <p>
        Or whatever it's going to be called ...
        Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
      </p>
      <p>Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium!</p>

    <h5 class="type--rock-salt">
        Connect
    </h5>
      <div class="flex-grid justify-center">
        <span class="clickable-icon">
          <mail-icon />
        </span>
        <span class="clickable-icon">
          <wifi-icon />
        </span>
        <span class="clickable-icon">
          <instagram-icon />
        </span>
      </div>
    </div>
    <!-- <div class="column">
          <g-image src="https://codex-themes.com/thegem/sites/travel-blog/wp-content/uploads/2019/05/4.png" alt="collage" />
    </div>-->
  </section>
</template>

<script>
import InstagramIcon from "~/assets/icons/instagram-icon.svg";
import WifiIcon from "~/assets/icons/wifi-icon.svg";
import MailIcon from "~/assets/icons/mail-icon.svg";

export default {
  components: {
    InstagramIcon,
    WifiIcon,
    MailIcon
  }
};
</script>

<style lang="scss">
.about-the-blog {
  padding: 1rem 1rem 2rem;
  background-color: var(--bg-content-color);
  flex-direction: column;

  .column {
    margin: 2rem 0;
  }

  .clickable-icon {
      cursor: pointer;
      margin: 0 .5rem;

      &:hover {
          transform: scale(1.2);
          transition: 0.3s ease;
      }
  }
}

@media screen and (min-width: 769px) {
  .about-the-blog {
    padding: 2rem;
    background-color: var(--bg-color);
    flex-direction: row;

    .column {
      margin: 2rem;
    }
  }
}
</style>