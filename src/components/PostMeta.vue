<template>
  <div class="post-meta">
    Posted {{ post.date }}.
    <template v-if="post.timeToRead">
      <clock-icon />
      <strong style="padding-left: 5px;">{{ post.timeToRead }} min read.</strong>
    </template>
  </div>
</template>

<script>
import ClockIcon from "~/assets/icons/clock-icon.svg";

export default {
  props: ["post"],
  components: {
    ClockIcon
  }
};
</script>

<style lang="scss">
.post-meta {
  font-size: 0.8em;
  opacity: 0.8;
}
</style>