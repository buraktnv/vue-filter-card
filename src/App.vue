<template>
  <filter-card :filter="filter"> </filter-card>
</template>

<script>
import FilterCard from "./components/FilterCard.vue";
import "../assets/css/main.css";
export default {
  name: "App",
  components: {
    FilterCard,
  },
  methods: {
    filter(pageObject) {
      console.log(pageObject);
    },
  },
};
</script>
