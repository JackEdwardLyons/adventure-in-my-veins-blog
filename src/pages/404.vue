<template>
  <main class="center-content">
    <div class="flex-column wrapper">
      <h1>404 page not found 😱</h1>
      <p>Maybe check the url for a typo and try again.</p>
      <p>
        Otherwise,
        <a href="/">click here to go home</a>, or sign up below to get notified when a new "digital dirtbag" article is released.
      </p>
      <mailchimp-form />
    </div>
  </main>
</template>

<script>
import MailchimpForm from "@/components/MailchimpForm";

export default {
  components: {
    MailchimpForm
  }
};
</script>

<style lang="scss" scoped>
.center-content {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin: 0 auto;
}

.wrapper {
  width: 90%;
  margin: 0 auto;
  @media screen and (min-width: 800px) {
    width: 700px;
  }
}
</style>