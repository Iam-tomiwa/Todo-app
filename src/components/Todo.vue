<template>
  <div class="todo-item">
    <div class="text">
      <label class="checkbox">
        <input type="checkbox" :id="id" />
      </label>
      <label :for="id" class="check-label">
        {{ itemName }}
      </label>
    </div>
    <button class="closeBtn">
      X
    </button>
  </div>
  <hr />
</template>

<script>
export default {
  name: "Header",
  emits: ["completed"],
  props: ["id", "itemName"],
  methods: {
    darkMode() {
      this.$emit("completed");
    },
  },
};
</script>
