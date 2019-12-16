<template>
  <section class="about-the-blog flex-grid text-center">
    <div class="column" style="margin: 0;">
      <g-image src="/images/demo-logo-2.png" alt="collage" style="margin-top: -2rem;" />
      <div style="position: relative; top: -3rem; max-width: 700px; margin: 0 auto;">
        <!-- <h2 class="type--rock-salt">Adventure In My Veins</h2> -->
        <p>
          An adventure publication crafted for those wanderlusting, thrill seeking,
          mountain lovers who want to build a location independent lifestyle. 
          I show you how to become a digital dirtbag and travel the world sustainably.
        </p>
      </div>


      </div>
    <!-- <div class="column">
    </div> -->
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
    margin: 0 0.5rem;

    &:hover {
      transform: scale(1.2);
      transition: 0.3s ease;
    }
  }
}

@media screen and (min-width: 769px) {
  .about-the-blog {
    padding: 0;
    background-color: var(--bg-color);
    flex-direction: row;

    .column {
      margin: 2rem;
    }
  }
}
</style>