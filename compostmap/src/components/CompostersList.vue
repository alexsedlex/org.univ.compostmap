<template>
  <div>
    <p class="columns">
      <button
        class="button is-primary"
        @click="composters.push({ id: (nextComposterId++).toString() })"
      >
        Add Composter {{ nextComposterId }}
      </button>
      <button
        class="button is-danger is-quarter"
        @click="composters.splice(0, 1)"
        v-if="composters.length > 0"
      >
        Remove composter {{ composters[0].id }}
      </button>
    </p>
    <div class="columns is-multiline">
      <Composter
        v-for="composter in composters"
        :key="composter.id"
        class="column is-half-tablet is-one-third-desktop is-one-quarter-widescreen"
        :composter="composter"
        @click="showComposterDetails(composter)"
      />
    </div>
  </div>
</template>

<script>
import Composter from "./Composter.vue";
// Import hard-coded list directly from json
import hardCodedCompostersList from "./hard-coded-data.json";

export default {
  name: "CompostersList",
  components: {
    Composter,
  },
  data() {
    return {
      nextComposterId: 1,
      // Use hard-coded list as data
      composters: hardCodedCompostersList,
    };
  },
  methods: {
    showComposterDetails(composter) {
      this.$router.push({
        name: "ComposterDetails",
        params: { id: composter.recordid },
      });
    },
  },
};
</script>
