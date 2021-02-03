<template>
  <div class="container is-fluid">
    <div class="columns is-multiline">
      <div class="column mt-4 is-full is-half-widescreen">
        <h1 class="title is-green">
          Progress en cours
        </h1>
        <h2 class="subtitle is-green mt-4 is-size-3">WoW Shadowlands</h2>
        <div class="link">
          <a href="https://wow.gdoc.fr">
            <figure class="image hover-green is-16by9 crop-to-fit">
              <img
                src="~/assets/images/events/2020/wow_shadowlands.jpg"
                alt="WoW Shadowlands"
              />
            </figure>
          </a>
        </div>
      </div>
      <div class="column mt-4 is-full  is-half-widescreen">
        <h2 class="title is-green">
          Précédent progress
        </h2>
        <h2 class="subtitle is-green mt-4 is-size-3">WoW BFA</h2>
        <div class="link">
          <a href="/events/2018/wow_bfa">
            <figure class="image hover-green crop-to-fit is-16by9 crop-to-fit">
              <img
                src="~/assets/images/events/2018/wow_bfa.jpg"
                alt="WoW BFA"
              />
            </figure>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({});
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";

.container {
  margin: 0 auto;
  min-height: 80vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.link {
  width: 60%;
  margin: auto;
}

.columns {
  width: 100%;
}
</style>
