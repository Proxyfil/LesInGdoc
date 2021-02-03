<template>
  <div class="container mt-4">
    <div class="columns is-multiline">
      <div class="column is-full" v-for="year in years" :key="year.year">
        <h1 class="title is-green">{{ year.year }}</h1>
        <div class="columns is-multiline is-centered">
          <div
            class="column is-full-tablet is-half-desktop is-half-widescreen is-one-third-fullhd"
            v-for="event in year.events"
            :key="year.year + '-' + event.name"
          >
            <div class="card no-shadow">
              <div class="card-header no-shadow">
                <div
                  class="card-header-title is-green is-centered no-shadow is-size-4"
                >
                  {{ event.name }}
                </div>
              </div>
              <div class="card-image">
                <a v-if="event.status != 'upcoming'" :href="get_gdoc_url(year.year, event)" target="_blank">
                  <figure
                    class="image is-5by3 crop-to-fit hover-green"
                  >
                    <img
                      :src="
                        require('~/assets/images/events/' +
                          year.year +
                          '/' +
                          event.slug +
                          '.jpg')
                      "
                      :alt="event.name"
                    />
                  </figure>
                </a>
								<figure
									v-else
                    class="image is-5by3 crop-to-fit hover-green upcoming"
                  >
                    <img
                      :src="
                        require('~/assets/images/events/' +
                          year.year +
                          '/' +
                          event.slug +
                          '.jpg')
                      "
                      :alt="event.name"
                    />

                    <div class="is-overlay is-green title has-text-centered pb-4">
                      <p>Coming Soon ...</p>
                    </div>
                  </figure>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  data() {
    return {
      years: require("~/data/events.json"),
    };
  },
  methods: {
    get_gdoc_url(year: string, event: any) {
      if (event.link_gdoc == undefined) {
        return event.link;
      }

      return "/events/" + year + "/" + event.slug;
    },
  },
});
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

.card {
  background: transparent;
}

.no-shadow {
  box-shadow: none;
}

.upcoming img {
  filter: grayscale(100%);
}

.upcoming p {
  position: absolute;
  bottom: 0;
  left: 0;
	right: 0;
	background-color: rgba(0, 0, 0, 0.7);
	height: 3rem;
}
</style>
