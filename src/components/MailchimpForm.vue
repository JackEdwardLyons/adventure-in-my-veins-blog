<template>
  <section class="shadow-md mailchimp">
    <h4 class="text-center" v-text="'Join the AIMV Community.'" />

    <div class="centered">
      <vue-typed-js 
        :strings="typedStrings" 
        :backSpeed="50"
        :typeSpeed="30"
        :backDelay="1000"
        :loop="true"
        class="text-center"
      >
        <p class="text-center">
          For those who want to
          <span class="typing"></span>
        </p>
      </vue-typed-js>
    </div>

    <!-- Mailchimp Signup -->
    <div class="error-message" v-show="message !== null">{{ message }}</div>
    <form :action="url" method="POST" novalidate target="_blank" v-on:submit="submitForm">
      <input name="EMAIL" type="email" :placeholder="placeholder" v-model="email" required />
      <button type="submit" v-text="'Subscribe'" />
    </form>
  </section>
</template>

<script>
import Vue from "vue";
import VueTypedJs from "vue-typed-js";

Vue.use(VueTypedJs);

export default {
  data() {
    return {
      message: null,
      email: null
    };
  },
  props: {
    success: {
      type: String,
      default: "Awesome, you're in!"
    },
    error: {
      type: String,
      default: "Please fix up your details!"
    },
    placeholder: {
      type: String,
      default: "Enter your email"
    },
    url: {
      type: String,
      default:
        "https://jacklyons.us16.list-manage.com/subscribe/post?u=9f82d3f200391b066ef73f021&amp;id=cf45a34209",
      required: false
    }
  },
  computed: {
    typedStrings () {
      return [
        'read more digital dirtbag posts ⛰.',
        'become a BETA user for my apps and web projects 🎮.',
        'join a global community of climbers 💪.',
        'climb by day and code by night 🖥.', 
        'learn how to become location independent 🌎.'
      ]
    }
  },
  methods: {
    submitForm(e) {
      if (this.email.length < 3 || this.email.indexOf("@") === -1) {
        this.message = this.error;
        e.preventDefault();
      }
    }
  }
};
</script>

<style lang="scss">
$white: #ffffff !default;
$brandColor: #5c97bf;

.centered {
  width: 90%;
  margin: 0 auto;
}

.email-capture {
  border: 1px solid #f1f1f1;
  text-align: center;
  padding: 3em;
  margin-top: 3em;
  margin-bottom: 3em;
  -webkit-border-radius: 4px;
  -moz-border-radius: 4px;
  border-radius: 4px;
  .form-group {
    width: 100%;
  }
}
.mailchimp {
  width: 100%;
  margin: 0 auto;

  input[type="email"] {
    width: 100%;
    background: #f5f5f5;
    height: 55px;
    padding: 18px 20px;
    font-size: 20px;
    margin-bottom: 15px;
    text-align: center;
    border: none;
    outline: none;
    color: #444;
    float: left;
    -webkit-appearance: none;
    -webkit-border-radius: 4px;
    -moz-border-radius: 4px;
    border-radius: 4px;
    -webkit-box-shadow: inset 0 -1px rgba(0, 0, 0, 0.1);
    -moz-box-shadow: inset 0 -1px rgba(0, 0, 0, 0.1);
    box-shadow: inset 0 -1px rgba(0, 0, 0, 0.1);
  }
  [type="submit"] {
    width: 100%;
    background-color: $brandColor;
    color: $white;
    font-size: 18px;
    height: 55px;
    border-radius: 4px;
    outline: none;
    border: 0;
    cursor: pointer;

    &:hover {
      background-color: darken($brandColor, 5%);
      transition: 0.3s ease;
    }
  }

  .error-message {
    color: #c53030;
    font-size: 90%;
  }
}
</style>
