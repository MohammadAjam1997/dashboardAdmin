<template>
  <div class="container top-0 position-sticky z-index-sticky">
    <div class="row">
      <div class="col-12">
        <navbar isBtn="bg-gradient-light" />
      </div>
    </div>
  </div>
  <main class="main-content mt-0">
    <div
      class="page-header align-items-start min-vh-50 pt-5 pb-11 m-3 border-radius-lg"
    >
      <span class="mask bg-gradient-dark opacity-6"></span>
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-lg-5 text-center mx-auto">
            <h1 class="text-white mb-2 mt-5">Welcome!</h1>
            <p class="text-lead text-white">
              Please register personal information to register a new user
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row mt-lg-n10 mt-md-n11 mt-n10 justify-content-center">
        <div class="col-xl-4 col-lg-5 col-md-7 mx-auto">
          <div class="card z-index-0">
            <div class="card-header text-center pt-4">
              <h5>Register</h5>
            </div>
            <div class="row px-xl-5 px-sm-4 px-3"></div>
            <div class="card-body">
              <form role="form">
                <label for="Name" class="form-label">Name</label>
                <input
                  id="Name"
                  v-model="Name"
                  class="form-control"
                  type="text"
                  placeholder="Name"
                  aria-label="default input example"
                />
                <label for="Phone" class="form-label">Phone</label>
                <input
                  id="Phone"
                  v-model="Phone"
                  class="form-control"
                  type="text"
                  placeholder="Phone"
                  aria-label="default input example"
                />
                <label for="email" class="form-label">Email</label>
                <input
                  id="email"
                  v-model="email"
                  class="form-control"
                  type="email"
                  placeholder="email"
                  aria-label="default input example"
                />
                <label for="Password" class="form-label">Password</label>
                <input
                  id="Password"
                  v-model="Password"
                  class="form-control"
                  type="password"
                  placeholder="Password"
                  aria-label="default input example"
                />
              </form>
              <div class="text-center">
                <button
                  @click="signUp()"
                  type="button"
                  class="btn btn-dark my-4 mb-2"
                >
                  Sign up
                </button>
              </div>

              <p class="text-sm mt-3 mb-0">
                Already have an account?
                <router-link class="text-success" to="/signin">
                  Sign in</router-link
                >
              </p>
            </div>
          </div>
          <!-- Button trigger modal -->
          <button
            type="button"
            class="btn btn-primary"
            id="myCheck"
            data-bs-toggle="modal"
            data-bs-target="#staticBackdrop"
            style="display: none;"
          >
            <!-- Launch static backdrop modal -->
          </button>

          <!-- Modal -->
          <div
            class="modal fade"
            id="staticBackdrop"
            data-bs-backdrop="static"
            data-bs-keyboard="false"
            tabindex="-1"
            aria-labelledby="staticBackdropLabel"
            aria-hidden="true"
          >
            <div class="modal-dialog">
              <div class="modal-content">
                <div class="modal-header">
                  <h5 class="modal-title" id="staticBackdropLabel">
                    Modal title
                  </h5>
                  <button
                    type="button"
                    class="btn-close"
                    data-bs-dismiss="modal"
                    aria-label="Close"
                  ></button>
                </div>
                <div class="modal-body">A new user has been created</div>
                <div class="modal-footer">
                  <button
                    type="button"
                    class="btn btn-secondary"
                    data-bs-dismiss="modal"
                  >
                    Close
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
<style scoped>
.page-header {
  background-image: url("../assets/img/card-visa.jpg");
  background-position: top;
}
</style>
<script>
import Navbar from "@/examples/PageLayout/Navbar.vue";
import axios from "axios";

const body = document.getElementsByTagName("body")[0];

export default {
  name: "signin",
  components: {
    Navbar,
  },
  data() {
    return {
      Name: "",
      Phone: "",
      Password: "",
      email: "",
      http: "http://15.237.7.54:8000/api/",
    };
  },
  methods: {
    myFunction() {
      console.log(document.getElementById("myCheck"));
      document.getElementById("myCheck").click();
    },
    signUp() {
      const options = {
        headers: {
          "content-type":
            "multipart/form-data; boundary=<calculated when request is sent>",
        },
      };
      const data = {
        mobile: this.Phone,
        password: this.Password,
        name: this.Name,
        email: this.email,
        balance: 10000,
        type: 1,
      };

      axios.post(`${this.http}createuser/`, data, options).then((res) => {
        console.log(res);
        this.myFunction();
      });
    },
  },
  created() {
    this.$store.state.hideConfigButton = true;
    this.$store.state.showNavbar = false;
    this.$store.state.showSidenav = false;
    this.$store.state.showFooter = false;
    body.classList.remove("bg-gray-100");
  },
  beforeUnmount() {
    this.$store.state.hideConfigButton = false;
    this.$store.state.showNavbar = true;
    this.$store.state.showSidenav = true;
    this.$store.state.showFooter = true;
    body.classList.add("bg-gray-100");
  },
};
</script>
