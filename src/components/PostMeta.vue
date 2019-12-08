<template>
   <div class="post-meta">
      Posted {{ post.date }}.
      <template v-if="post.timeToRead">
        <clock-icon />
        <strong> {{ post.timeToRead }} min read.</strong>
      </template>
    </div>
</template>

<script>
import ClockIcon from "~/assets/icons/clock-icon.svg";

export default {
  props: ['post'],
  components: {
    ClockIcon
  }
}
</script>

<style lang="scss">
.post-meta {
  font-size: .8em;
  opacity: .8;
}
</style>