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

          <component :is="'app-full-name'" v-model="user.fullName"></component>

          <div class="form-group">
            <label for="inputMail">Mail</label>
            <input type="email" class="form-control" id="inputMail" v-model="user.mail" />
            <small class="form-text text-muted">Your e-mail is safe with us</small>
          </div>

          <div class="form-group">
            <label for="inputPassword">Password</label>
            <input type="password" class="form-control" id="inputPassword" v-model="user.password" />
          </div>

          <div class="form-check">
            <input
              type="checkbox"
              class="form-check-input"
              id="storeData"
              value="storeData"
              v-model="user.storeData"
            />
            <label for="storeData" class="form-check-label">Store Data?</label>
          </div>

          <div class="w-100 mt-4 mb-1 text-secondary">Just some radio buttons</div>
          <div class="form-check form-check-inline">
            <input
              type="radio"
              class="form-check-input"
              name="radiotests"
              id="radio1"
              value="Yes"
              v-model="user.RadioTest"
            />
            <label class="form-check-label" for="radio1">Yes</label>
          </div>

          <div class="form-check form-check-inline">
            <input
              type="radio"
              class="form-check-input"
              name="radiotests"
              id="radio2"
              value="No"
              v-model="user.RadioTest"
            />
            <label class="form-check-label" for="radio2">No</label>
          </div>

          <div class="form-check form-check-inline">
            <input
              type="radio"
              class="form-check-input"
              name="radiotests"
              id="radio3"
              value="Later"
              v-model="user.RadioTest"
            />
            <label class="form-check-label" for="radio3">Maybe later</label>
          </div>
          <div class="w-100"></div>
          <button class="btn btn-primary mt-4" @click.prevent="isSubmitted = true">Submit</button>
        </div>
      </div>
    </form>
    <div v-if="isSubmitted" class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="card">
          <div class="card-header">
            <h4>Your Data</h4>
          </div>
          <div class="card-body">
            <p>Full Name: {{ user.fullName }}</p>
            <p>Mail: {{ user.mail }}</p>
            <p>Password: {{ user.password }}</p>
            <p>Store in Database?</p>
            <ul>
              <li v-for="(sdata, index) in user.storeData" :key="index">{{ sdata }}</li>
            </ul>
            <p>
              Radio Chosen:
              {{ user.RadioTest }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FullName from "./components/FullName.vue";

export default {
  components: {
    "app-full-name": FullName
  },
  data() {
    return {
      user: {
        fullName: "Fred Mirrors",
        firstName: "Goffrey",
        lastName: "Smiths",
        mail: "goff.smiths@mail.com",
        password: "goffspass",
        storeData: ["storeData"],
        RadioTest: "Yes"
      },
      isSubmitted: false
    };
  }
};
</script>

<style>
</style>
