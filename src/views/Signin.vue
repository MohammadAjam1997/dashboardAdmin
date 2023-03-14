<template>
  <div class="container top-0 position-sticky z-index-sticky">
    <div class="row">
      <div class="col-12">
        <navbar
          isBlur="blur  border-radius-lg my-3 py-2 start-0 end-0 mx-4 shadow"
          v-bind:darkMode="true"
          isBtn="bg-gradient-success"
        />
      </div>
    </div>
  </div>
  <main class="mt-0 main-content">
    <section>
      <div class="page-header min-vh-100">
        <div class="container">
          <div class="row">
            <div
              class="mx-auto col-xl-4 col-lg-5 col-md-7 d-flex flex-column mx-lg-0"
            >
              <div class="card card-plain">
                <div class="pb-0 card-header text-start">
                  <h4 class="font-weight-bolder">Sign In</h4>
                  <p class="mb-0">Enter your email and password to sign in</p>
                </div>
                <div class="card-body">
                  <form role="form">
                    <div class="mb-3">
                      <input
                        id="Name"
                        v-model="Phone"
                        class="form-control"
                        type="text"
                        placeholder="Name"
                        aria-label="default input example"
                      />
                    </div>
                    <div class="mb-3">
                      <input
                        id="Name"
                        v-model="Password"
                        class="form-control"
                        type="text"
                        placeholder="Password"
                        aria-label="default input example"
                      />
                    </div>
                  </form>
                </div>
                <div class="d-flex justify-content-center">
                  <button
                    @click="signIn()"
                    type="button"
                    class="btn btn-success px-5"
                  >
                    Sign in
                  </button>
                </div>

                <div class="px-1 pt-0 text-center card-footer px-lg-2">
                  <p class="mx-auto mb-4 text-sm">
                    Don't have an account?
                    <router-link class="text-success" to="/signup">
                      Sign up</router-link
                    >
                  </p>
                </div>
              </div>
            </div>
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
                  <div class="modal-body">Success Log In</div>
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
            <!-- <button @click="signIn()">Sign in</button> -->

            <div
              class="top-0 my-auto text-center col-6 d-lg-flex d-none h-100 pe-0 position-absolute end-0 justify-content-center flex-column"
            >
              <div
                class="position-relative bg-gradient-primary h-100 m-3 px-7 border-radius-lg d-flex flex-column justify-content-center overflow-hidden"
                style="
                  background-image: url('https://raw.githubusercontent.com/creativetimofficial/public-assets/master/argon-dashboard-pro/assets/img/signin-ill.jpg');
                  background-size: cover;
                "
              >
                <span class="mask bg-gradient-success opacity-6"></span>
                <h4
                  class="mt-5 text-white font-weight-bolder position-relative"
                >
                  "Attention is the new currency"
                </h4>
                <p class="text-white position-relative">
                  The more effortless the writing looks, the more effort the
                  writer actually put into the process.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
  <button
    id="myCheck"
    style="display: none"
    type="button"
    class="btn btn-primary"
    data-bs-toggle="modal"
    data-bs-target="#exampleModal"
  ></button>

  <!-- Modal -->
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">LogIn Success</div>
        <div class="modal-footer">
         <router-link to="/dashboard-default">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
            
          >
            Ok
          </button>
        </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/examples/PageLayout/Navbar.vue";
import axios from "axios";
import { mapActions } from "vuex";

const body = document.getElementsByTagName("body")[0];

export default {
  name: "signin",
  components: {
    Navbar,
  },
  data() {
    return {
      Phone: "",
      Password: "",
      http: "http://15.237.7.54:8000/api/",
    };
  },

  methods: {
    ...mapActions(["DataOflogin"]),
    myFunction() {
      console.log(document.getElementById("myCheck"));
      document.getElementById("myCheck").click();
    },
    signIn() {
      const options = {
        headers: {
          "content-type":
            "multipart/form-data; boundary=<calculated when request is sent>",
        },
      };
      const data = { mobile: this.Phone, password: this.Password };
      axios.post(`${this.http}login/`, data, options).then((res) => {
        this.DataOflogin(res.data);
        this.myFunction();
      });
    },
  },
  created() {
    // axios.get(`${this.http}history?pk=1`).then((res) => {
    //   console.log(res);
    // });
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
<style scoped>
.btn-success {
  width: 75%;
}
</style>
