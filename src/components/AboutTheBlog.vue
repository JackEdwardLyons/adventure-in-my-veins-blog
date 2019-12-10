<template>
  <section class="about-the-blog grid ">
      <div class="column">
          <h2 class="rock-salt">
              Meet the Digital Dirtbag ... 
          </h2>
          <p>
              Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
          </p>
          <p>
              Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium!
          </p>
          <p>
              <strong>
                  Follow me on Instagram ... 
              </strong>
          </p>
          <p>
              <strong>
                  Become a Digital Dirtbag ...
              </strong>
          </p>
          <p>
              <strong>
                  Join the community ...
              </strong>
          </p>
          <p>
              <strong>
                  Contact me ...
              </strong>
          </p>
      </div>
      <div class="column">
          <img src="https://codex-themes.com/thegem/sites/travel-blog/wp-content/uploads/2019/05/4.png" alt="collage" />
      </div>
  </section>
</template>

<script>
export default {

}
</script>

<style lang="scss">
.about-the-blog {
    padding: 1rem 1rem 2rem;
    background-color: var(--bg-content-color);

    .column {
        margin: 2rem 0;
    }
}

@media screen and (min-width: 769px) {
    .about-the-blog {
        padding: 2rem;
        background-color: var(--bg-color);

        .column {
            margin: 2rem;
        }
    }
}
</style>