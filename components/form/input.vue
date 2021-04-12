<template>
  <div class="form-group">
    <label>{{name}}</label>
    <input type="text" class="form-control" v-model="value">
  </div>
</template>
<script>
export default {
  props: {
    name: { type: String, default: "Default Input Text" },
    val: { type: String, default: "" },
  },
  computed: {
    value: {
      get() {
        return this.val;
      },
      set(value) {
        this.$emit("value", value);
      },
    },
  },
};
</script>