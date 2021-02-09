<template>
  <img :src="themeImage" class="bg-image" alt="" />
  <div class="header">
    <h1>TODO</h1>
    <img :src="themeIcon" class="darkmode-icon" @click="darkMode" alt="" />
  </div>
</template>

<script>
export default {
  name: "Header",
  emits: ["toggleTheme"],
  props: ["themeIcon", "themeImage"],
  methods: {
    darkMode() {
      this.$emit("toggleTheme");
    },
  },
};
</script>
