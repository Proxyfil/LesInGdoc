<template>
  <div class="container mt-4">
    <div class="columns is-multiline">
      <div
        class="column is-half-tablet is-one-third-desktop is-one-quarter-widescreen is-one-fifth-fullhd"
        v-for="person in team"
        :key="person.name"
      >
        <div class="card profile">
          <div class="card-image">
            <figure class="image is-square crop-to-fit">
              <img
                :src="require('~/assets/images/team/' + person.name + '.png')"
                :alt="person.name"
              />
            </figure>
          </div>
          <div class="card-content">
            <p class="title is-4 is-white">{{ person.name }}</p>
            <p class="subtitle is-5 is-green">{{ person.position }}</p>
          </div>
          <footer class="card-footer pb-2">
            <div v-if="person.socials.discord" class="card-footer-item social">
              <span class="icon is-medium flex mb-1">
                <img
                  src="https://www.flaticon.com/svg/static/icons/svg/2111/2111370.svg"
                  alt=""
                />
              </span>
              <p class="flex is-discord">
                {{ person.socials.discord }}
              </p>
            </div>

            <a
              v-if="person.socials.twitter"
              :href="'https://twitter.com/' + person.socials.twitter"
              target="_blank"
              class="card-footer-item social"
            >
              <span class="icon is-medium mb-1">
                <img
                  src="https://www.flaticon.com/svg/static/icons/svg/733/733579.svg"
                  alt=""
                />
              </span>
              <p class="flex is-twitter">
                {{ person.socials.twitter }}
              </p>
            </a>
          </footer>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" scoped>
import Vue from "vue";

export default Vue.extend({
  data() {
    return {
      team: require("~/data/team.json"),
    };
  },
});
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  justify-content: center;
  text-align: center;
}
</style>
