<template>
  <div class="container mx-auto">
    <form v-if="!isSubmitted">
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-12">
          <!-- Exercise 1 -->
          <!-- Create a Signup Form where you retrieve the following Information -->
          <!-- Full Name (First Name + Last Name) -->
          <!-- Mail -->
          <!-- Password -->
          <!-- Store Data? Yes/No -->

          <!-- Exercise 2 -->
          <!-- Only display the Form if it has NOT been submitted -->
          <!-- Display the Data Summary ONCE the Form HAS been submitted -->

          <!-- Exercise 3 -->
          <!-- Edit the Example from above and create a custom "Full Name" Control -->
          <!-- which still holds the First Name and Last Name Input Field -->

          <component :is="'get-full-name'" v-model="user.fullName"></component>

          <div class="form-group">
            <label for="inputfirstName">First Name</label>
            <input type="text" class="form-control" id="inputfirstName" v-model="user.firstName" />
          </div>

          <div class="form-group">
            <label for="inputlastName">Last Name</label>
            <input type="text" class="form-control" id="inputlastName" v-model="user.lastName" />
          </div>

          <div class="form-group">
            <label for="inputMail">Mail</label>
            <input type="email" class="form-control" id="inputMail" v-model="user.mail" />
            <small class="form-text text-muted">Your e-mail is safe with us</small>
          </div>

          <div class="form-group">
            <label for="inputPassword">Password</label>
            <input type="password" class="form-control" id="inputPassword" v-model="user.password" />
          </div>

          <div class="form-group form-check">
            <input
              type="checkbox"
              class="form-check-input"
              id="inputStoreData"
              v-model="user.storeData"
            />
            <label for="inputStoreData" class="form-check-label">Store Data?</label>
          </div>

          <button class="btn btn-primary" @click.prevent="isSubmitted = true">Submit</button>
        </div>
      </div>
    </form>
    <hr />
    <div v-if="isSubmitted" class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="card">
          <div class="card-header">
            <h4>Your Data</h4>
          </div>
          <div class="card-body">
            <p>Full Name: {{ user.fullName }}</p>
            <p>First Name: {{ user.firstName }}</p>
            <p>Last Name: {{ user.lastName }}</p>
            <p>Mail: {{ user.mail }}</p>
            <p>Password: {{ user.password }}</p>
            <p>Store in Database? {{ user.storeData }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GetFullName from "./components/GetFullName.vue";

export default {
  components: {
    "get-full-name": GetFullName
  },
  data() {
    return {
      user: {
        fullName: "Goffrey Smiths",
        firstName: "Goffrey",
        lastName: "Smiths",
        mail: "goff.smiths@mail.com",
        password: "goffspass",
        storeData: false
      },
      isSubmitted: false
    };
  }
};
</script>

<style>
</style>
