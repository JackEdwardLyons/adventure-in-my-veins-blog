<template>
  <section class="shadow-md mailchimp">
    <h4 class="text-center m-0 my-1" v-text="subscribeMsg" />

    <div class="centered" v-if="animated">
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
    <form
      class="flex-grid mailchimp-form"
      :action="url"
      method="POST"
      novalidate
      target="_blank"
      v-on:submit="submitForm"
    >
      <div class="input-flex">
        <label for="mce-FNAME" hidden>First Name</label>
        <input id="mce-FNAME" name="FNAME" type="text" v-model="firstName" placeholder="First Name" />
        <label for="mce-FNAME" hidden>Last Name</label>
        <input id="mce-LNAME" name="LNAME" type="text" v-model="lastName" placeholder="Last Name" />
      </div>
      <div class="input-flex">
        <label for="mce-EMAIL" hidden>Email Address</label>
        <input
          id="mce-EMAIL"
          name="EMAIL"
          type="email"
          :placeholder="placeholder"
          v-model="email"
          required
        />
        <button type="submit" v-text="'Subscribe'" />
      </div>
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
      email: "",
      firstName: "",
      lastName: ""
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
    },
    animated: {
      type: Boolean,
      default: true
    },
    subscribeMsg: {
      type: String,
      default: "Join the Digital Dirtbag Community today!"
    }
  },
  computed: {
    typedStrings() {
      return [
        "climb around the world without 🔥 all your 💵.",
        "read more digital dirtbag posts ⛰.",
        "become a BETA user for my web apps 🎮.",
        "join a 🌎 community of climbers 💪.",
        "climb by day and code by night 🖥.",
        "learn how to become location independent 🌎."
      ];
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

.mailchimp {
  width: 100%;
  margin: 0 auto;

  .input-flex {
    display: flex;
    width: 100%;

    #mce-LNAME {
      margin-left: 1rem;
    }

    @media screen and (max-width: 769px) {
      flex-wrap: wrap;

      #mce-LNAME {
        margin-left: 0;
      }
    }
  }

  input {
    width: 100%;
    background: #f5f5f5;
    height: 55px;
    padding: 18px 20px;
    font-size: 20px;
    margin-bottom: 15px;
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
    margin-left: 0;
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

  @media screen and (min-width: 769px) {
    input[type="email"] {
      // width: 70%;
    }

    [type="submit"] {
      width: auto;
      min-width: 150px;
      margin-left: 1rem;
    }
  }

  .error-message {
    color: #c53030;
    font-size: 90%;
  }
}
</style>
