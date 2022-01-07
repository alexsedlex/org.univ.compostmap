<template>
  <div>
    <h1>Détails du composteur {{ id }}</h1>
    <Composter v-if="!isLoading" :composter="composter" />
    <p v-else>Chargement en cours...</p>
  </div>
</template>

<script>
import Composter from "./Composter.vue";
// Import hard-coded list directly from json
import hardCodedCompostersList from "./hard-coded-data.json";

export default {
  name: "ComposterDetailPage",
  props: {
    id: String,
  },
  data() {
    // Find the composter on which this detail view is focused
    var focusedComposter = hardCodedCompostersList.filter(
      (composter) => composter.recordid == this.id
    );
    return {
      isLoading: false,
      composter: focusedComposter[0],
    };
  },
  components: {
    Composter,
  },
};
</script>
