<template>
  <Layout>
    <the-header />
    
    <div class="post-title">
      <h1 class="post-title__text">{{ $page.post.title }}</h1>
      <PostMeta :post="$page.post" />
    </div>

    <div class="post content-box">
      <div class="post__header">
        <g-image alt="Cover image" v-if="$page.post.cover_image" :src="$page.post.cover_image" />
      </div>

      <div class="post__content" v-html="$page.post.content" />

      <div class="post__footer">
        <PostTags :post="$page.post" />
      </div>

      <div class="signup-area">
        <mailchimp-form />
      </div>
    </div>

    <div class="post-comments">
      <!-- Add comment widgets here -->
    </div>
  </Layout>
</template>

<script>
import PostMeta from "~/components/PostMeta";
import PostTags from "~/components/PostTags";
import TheHeader from '~/components/TheHeader';
import MailchimpForm from '~/components/MailchimpForm';

export default {
  components: {
    PostMeta,
    PostTags,
    TheHeader,
    MailchimpForm
  },
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: "description",
          content: this.$page.post.description
        },
        {
          property: "og:title",
          content: this.$page.post.title
        },
        {
          name: "twitter:card",
          content: this.$page.post.image ? "summary_large_image" : "summary",
        },
        // {
        //   name: "twitter:creator",
        //   content: "@drewtown_chi"
        // },
        {
          property: "og:description",
          cotent: this.$page.post.excerpt
        },
        {
          property: "og:image",
          content: this.$page.post.image || ""
        }
      ]
    };
  }
};
</script>

<page-query>
query Post ($id: ID!) {
  post: post (id: $id) {
    title
    path
    date (format: "D. MMMM YYYY")
    timeToRead
    tags {
      id
      title
      path
    }
    description
    content
    cover_image (width: 860, blur: 10)
  }
}
</page-query>

<style lang="scss">
.post-title {
  padding: calc(var(--space) / 2) var(--space);
  text-align: center;
  max-width: 800px;
  text-align: center;
  margin: 0 auto;
}

.post {
  &__header {
    width: calc(100% + var(--space) * 2);
    margin-left: calc(var(--space) * -1);
    margin-top: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    img {
      width: 100%;
    }

    &:empty {
      display: none;
    }
  }

  &__content {

    h2 {
      font-size: 1.5rem;
      line-height: 1.4;

      &:first-child {
        margin-top: 0;
      }
    }

    p:first-of-type {
      font-size: 1.2em;
      color: var(--title-color);
    }

    img {
      width: calc(100% + var(--space) * 2);
      margin-left: calc(var(--space) * -1);
      display: block;
      max-width: none;
    }
  }
}

.post-comments {
  padding: calc(var(--space) / 2);

  &:empty {
    display: none;
  }
}

.post-author {
  margin-top: calc(var(--space) / 2);
}

.signup-area {
  margin-top: 3rem;
  border-top: 1px solid lightgrey;
}
</style>
