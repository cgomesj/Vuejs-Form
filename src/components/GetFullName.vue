<template>
  <div class="form-row">
    <div class="form-group col-md-12">
      <label for="getFirstName">Full Name</label>
      <input
        type="text"
        class="form-control"
        id="getFirstName"
        @input="setFulltName"
        :value="value"
      />
      <small class="form-text text-muted">{{ value }}</small>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: String
  },

  methods: {
    setFulltName($event) {
      this.$emit("input", $event.target.value);
    }
  }
};
</script>

<style scoped>
</style>