<template>
  <div>
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item navbar-logo" href="/">
          <img src="~/assets/images/logo.png" />
        </a>
        <a
          role="button"
          class="navbar-burger burger is-large"
          :class="{ 'is-active': is_menu_active }"
          aria-label="menu"
          aria-expanded="false"
          data-target="main-menu"
          @click="toggle_menu"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="main-menu" class="navbar-menu" :class="{ 'is-active': is_menu_active }">
        <div class="navbar-start">
          <nuxt-link to="/" class="navbar-item"> Accueil </nuxt-link>

          <nuxt-link to="/events" class="navbar-item"> Les Gdocs </nuxt-link>

          <nuxt-link to="/team" class="navbar-item"> L'équipe </nuxt-link>

          <nuxt-link to="/about" class="navbar-item"> A propos </nuxt-link>
        </div>
      </div>
    </nav>

    <Nuxt />
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  data() {
    return {
      menu: false
    }
  },
  computed: {
    is_menu_active() {
      return (this as any).menu;
    }
  },
  methods: {
    toggle_menu() {
      (this as any).menu = !(this as any).menu;
    }
  }
});
</script>

<style>
</style>
