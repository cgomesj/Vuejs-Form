<template>
  <div>
    <div class="form-group">
      <label for="inputfirstName">First Name</label>
      <input
        type="text"
        class="form-control"
        id="inputfirstName"
        :value="firstName"
        @input="updateName($event, 0)"
      />
    </div>

    <div class="form-group">
      <label for="inputlastName">Last Name</label>
      <input
        type="text"
        class="form-control"
        id="inputlastName"
        :value="lastName"
        @input="updateName($event, 1)"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: ["value"],

  computed: {
    firstName() {
      return this.value.split(" ")[0];
    },

    lastName() {
      return this.value.split(" ")[1];
    }
  },

  methods: {
    updateName($event, mode) {
      let name = "";

      if (!mode) {
        name = $event.target.value + " " + this.lastName;
      } else {
        name = this.firstName + " " + $event.target.value;
      }

      this.$emit("input", name);
    }
  }
};
</script>

<style  scoped>
</style>