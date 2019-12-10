<template>
  <article class="post-container">
    <div class="post-meta">
      <div class="post-read-time">
        <clock-icon />
        <span style="padding-left: 5px;">{{ post.node.timeToRead }} min read.</span>
      </div>
      <span class="post-date">{{ simpleDate(post.node.date) }}</span>
    </div>
    <h2 class="post-title">{{ post.node.title }}</h2>
    <hr class="post-title-divider" />
    <p v-if="showDesc" class="post-description">{{ truncated(post.node.description) }}</p>
  </article>
</template>

<script>
import ClockIcon from "~/assets/icons/clock-icon.svg";

export default {
  props: {
    post: {
      type: Object,
      required: true,
      default: () => ({})
    },
    showDesc: {
      type: Boolean,
      required: false,
      default: true
    },
    maxChars: {
      type: Number,
      default: 140,
      required: false
    }
  },
  components: {
    ClockIcon
  },
  computed: {
    simpleDate() {
      return date => {
        // => October 2019
        return date
          .split(" ")
          .slice(1)
          .join(" ");
      };
    },
    truncated() {
      return desc => {
        const MAX_CHARS = this.maxChars;
        return desc.length > MAX_CHARS
          ? desc.slice(0, MAX_CHARS) + " ..."
          : desc;
      };
    }
  }
};
</script>

<style lang="scss">
.post-container {
  padding: 1rem;

  
  * {
    color: #fff;
    text-align: center;
  }

  .post-meta {
    display: flex;
    justify-content: space-between;
    width: 200px;
    font-size: 70%;
    margin: 0 auto;
  }

  .post-date {
    margin: 0;
    font-size: 90%;
  }

  .post-description {
    display: none;
    max-width: 80%;
    margin: 0 auto 0.5rem auto;
    font-size: 90%;
    color: #fcfaf5;
    opacity: 0.8;
  }

  .post-title-divider {
    width: 50%;
    margin-top: 0;
    margin-left: auto;
    margin-right: auto;
    border: 0.5px solid rgba(255, 255, 255, 0.4);
    display: none;
  }

  .post-title {
    margin: 0rem auto;
    padding: 0.5rem 0;
    font-size: 1.25rem;
  }
}

@media screen and (min-width: 769px) {
  .post-container {
    .post-description {
      display: block;
    }
    .post-meta {
      width: 300px;
    }
    .post-title-divider {
      display: block;
    }
    .post-title {
      font-size: 1.8rem;
    }
  }
}
</style>