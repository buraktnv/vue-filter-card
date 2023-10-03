<template>
  <div class="wrapper">
    <form id="filter-card" class="filter-card" @submit.prevent="submitForm">
      <p class="title">Filter</p>
      <div class="filter-card__item">
        <label for="location" class="title -sub">Location</label>
        <input
          type="text"
          name="location"
          class="input -location"
          id="location"
          placeholder="Eg. London"
          v-model="location"
        />
      </div>
      <div class="filter-card__item">
        <label class="title -sub">Experience Level</label>
        <div class="filter-card__input-group">
          <div class="input-group">
            <input
              class="input -checkbox"
              type="checkbox"
              id="level-1"
              name="level"
              value="1-2"
              v-model="level"
            />
            <label for="level-1"> 1-2 Years Experience</label>
          </div>
          <div class="input-group">
            <input
              class="input -checkbox"
              type="checkbox"
              id="level-2"
              name="level"
              value="3-5"
              v-model="level"
            />
            <label for="level-2"> 3-5 Years Experience</label>
          </div>
          <div class="input-group">
            <input
              class="input -checkbox"
              type="checkbox"
              id="level-3"
              name="level"
              value="6-8"
              v-model="level"
            />
            <label for="level-3"> 6-8 Years Experience</label>
          </div>
          <div class="input-group">
            <input
              class="input -checkbox"
              type="checkbox"
              id="level-4"
              name="level"
              value="9+"
              v-model="level"
            />
            <label for="level-4"> 9+ Years Experience</label>
          </div>
        </div>
      </div>

      <div class="filter-card__item">
        <label class="title -sub">Target</label>
        <div class="filter-card__input-group">
          <div class="input-group">
            <input
              class="input -checkbox"
              type="checkbox"
              name="target"
              id="freelancer"
              value="freelancer"
              v-model="target"
            />
            <label for="freelancer">Freelancer</label>
          </div>
          <div class="input-group">
            <input
              class="input -checkbox"
              type="checkbox"
              name="target"
              v-model="target"
              id="agency"
              value="agency"
            />
            <label for="agency">Agency</label>
          </div>
        </div>
      </div>

      <button type="submit" class="button" :disabled="isFormInvalid">
        Submit
      </button>
    </form>
  </div>
</template>

<script>
import { toRaw } from "vue";

export default {
  props: ["filter"],
  computed: {
    isFormInvalid() {
      return (
        !this.location ||
        !toRaw(this.level).length ||
        !toRaw(this.target).length
      );
    },
  },
  data() {
    return {
      location: "",
      level: [],
      target: [],
    };
  },
  methods: {
    submitForm() {
      if (
        !this.location ||
        !toRaw(this.level).length ||
        !toRaw(this.target).length
      ) {
        alert("Please fill the form.");
        return;
      }

      this.filter({
        location: this.location,
        level: toRaw(this.level),
        target: toRaw(this.target),
      });
    },
  },
};
</script>
