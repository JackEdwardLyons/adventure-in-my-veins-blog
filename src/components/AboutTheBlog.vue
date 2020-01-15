<template>
  <section class="about-the-blog flex-grid text-center">
    <div class="column" style="margin: 0;">
      <g-image :src="this.logoUrl" alt="AIMV logo" class="aimv-logo mt-4" />
      <div style="max-width: 700px; margin: 0 auto;">
        <hr style="max-width: 100px; color: rgba(0, 0, 0, 0.5);" />
        <p class="my-2">
          An adventure publication crafted for rock climbers and mountain lovers who want to travel the world &amp; build a location independent lifestyle.

          <br /><br>Here you'll find tips on how to learn a creative or digital skill (like coding), build a portfolio and become a freelancer, work remotely or even start your own online business from scratch, all while travelling (<em>climbing</em>) around the world 🚀
          <a
            class="text-link"
            href="https://jacklyons.us16.list-manage.com/subscribe/post?u=9f82d3f200391b066ef73f021&amp;id=cf45a34209"
          >Click here to join the digital dirtbag community today!</a>
        </p>
        <!-- 
        * Dirtbag: Someone who forgoes material comforts and defies societal norms in pursuit of a nomadic mountaineering lifestyle.
        -->
      </div>
    </div>
    <!-- <div class="column">
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
  },
  data() {
    return {
      logoUrl: ""
    };
  },
  mounted() {
    var style = getComputedStyle(document.body);
    this.logoUrl = JSON.parse(style.getPropertyValue("--logo"));
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

.text-link {
  position: relative;
  display: inline-block;
  clear: both;
  position: relative;
  z-index: 1;
  // text-decoration: none;
  // color: var(--link-color);
}
</style>