<template>
  <div>
    <div class="container">
      <span class="icon is-large">
        <i class="fas fa-spinner fa-pulse fa-3x"></i>
      </span>
    </div>
    <iframe :src="event.link_gdoc" frameBorder="0"></iframe>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

import { Context } from "@nuxt/types";

export default Vue.extend({
  layout: "blank",
  async asyncData(context: Context) {
    const params = context.route.params;

    const years = require("~/data/events.json");

    let year_selected = undefined;
    let event_selected = undefined;

    for (let year of years) {
      if (year.year == params.year) {
        year_selected = year;
        break;
      }
    }

    if (year_selected == undefined) {
      context.redirect("/events");

      return;
    }

    for (let event of year_selected.events) {
      if (event.slug == params.slug) {
        event_selected = event;
        break;
      }
    }

    if (event_selected == undefined) {
      context.redirect("/events");

      return;
    }

    return {
      event: event_selected,
    };
  },
});
</script>

<style lang="scss" scoped>
.container {
  margin: 0 auto;
  min-height: 80vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

iframe {
  max-width: 100%;
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 9999999999999;
  top: 0;
  left: 0;
}
</style>
