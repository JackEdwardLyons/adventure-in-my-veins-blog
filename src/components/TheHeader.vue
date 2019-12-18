<template>
  <header class="header">
    <div class="header__left">
      <Logo v-if="showLogo" />
    </div>

    <div class="header__right">
      <ToggleTheme />
    </div>
  </header>
</template>

<script>
import Logo from "~/components/Logo.vue";
import ToggleTheme from "~/components/ToggleTheme.vue";

export default {
  components: {
    ToggleTheme,
    Logo
  },
  props: {
    showLogo: {
      type: Boolean,
      default: true
    }
  }
};
</script>
