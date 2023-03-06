<template>
  <div class="search-box">
    <input
      type="text"
      class="search-bar"
      placeholder="Enter your location..."
      v-model="location"
      @keypress="(event) => onSubmit(event, location)"
    />
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  props: ["onSubmit"],
  data() {
    return {
      location: "",
    };
  },
};
</script>
