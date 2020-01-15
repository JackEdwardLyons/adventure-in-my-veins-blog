<template>
  <article class="flex-grid my-1 social-sharing">
    <social-sharing
      :url="postUrl"
      :title="$page.post.title"
      :description="$page.post.description"
      :quote="$page.post.description"
      :hashtags="postTags"
      :media="$page.post.cover_image"
      inline-template
    >
      <div class="social-sharing__icons">
        <p class="share-this"> 
          <strong >Share this post:</strong>
        </p>
        <network network="facebook">
          <g-image
            alt="Facebook logo"
            title="Share on Facebook"
            class="icon facebook-icon"
            src="/icons/social/facebook-icon.svg"
          />
        </network>
        <network network="twitter">
          <g-image
            alt="Twitter logo"
            title="Share on Twitter"
            class="icon twitter-icon"
            src="/icons/social/twitter-icon.svg"
          />
        </network>
        <network network="reddit">
          <g-image
            alt="Reddit logo"
            title="Share on Reddit"
            class="icon reddit-icon"
            src="/icons/social/reddit-icon.svg"
          />
        </network>
        <network network="linkedin">
          <g-image
            alt="LinkedIn logo"
            title="Share on LinkedIn"
            class="icon linkedin-icon"
            src="/icons/social/linkedin-icon.svg"
          />
        </network>
        <network network="pinterest">
          <g-image
            alt="Pinterest logo"
            title="Share on Pinterest"
            class="icon pinterest-icon"
            src="/icons/social/pinterest-icon.svg"
          />
        </network>
      </div>
    </social-sharing>
  </article>
</template>

<script>
export default {
  computed: {
    postUrl() {
      return "https://www.adventureinmyveins.com" + this.$page.post.path;
    },
    postTags() {
      return this.$page.post.tags.map(post => post.title).join(",");
    }
  }
};
</script>

<style lang="scss">
.share-this {
  margin-bottom: 0.5rem;
}
</style>