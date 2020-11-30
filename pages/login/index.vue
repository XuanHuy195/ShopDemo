<template>
  <div class="bg-primary">
    <b-container fluid="lg">
      <b-row class="justify-content-center">
        <b-col col lg="12" xl="10" md="9">
          <div class="my-5 p-0 m-0">
            <b-card>
              <b-row class="m-0">
                <b-col lg="6" class="d-none d-lg-block p-0">
                  <b-card
                    img-src="@/assets/img/photo-dog-login.jpg"
                    class="bg-login-image h-50"
                  />
                </b-col>
                <b-col col lg="6" class="px-5">
                  <h3 class="text-center my-4">Welcome Back!</h3>
                  <b-form-group
                    id="input-group-1"
                    label-for="input-1"
                    class="mb-4"
                  >
                    <b-form-input
                      id="input-1"
                      type="email"
                      v-model="email"
                      required
                      :state="null"
                      placeholder="Enter email address..."
                    ></b-form-input>
                  </b-form-group>
                  <b-form-group
                    id="input-group-1"
                    label-for="input-1"
                    class="mb-4"
                    :state="null"
                  >
                    <b-form-input
                      id="input-1"
                      type="password"
                      v-model="password"
                      required
                      placeholder="Password"
                    ></b-form-input>
                  </b-form-group>
                  <b-form-checkbox
                    id="checkbox-1"
                    name="checkbox-1"
                    value="accepted"
                    unchecked-value="not_accepted"
                  >
                    Remember me!
                  </b-form-checkbox>

                  <b-button
                    block
                    variant="primary"
                    class="my-4"
                    @click="login()"
                    >Login</b-button
                  >
                  <hr />
                  <b-button block variant="danger" class="mb-4"
                    >Login with Google</b-button
                  >
                  <b-button block class="btn-facebook"
                    >Login with Facebook</b-button
                  >
                  <hr />
                  <div class="text-center mt-4">
                    <a href="#">Forgot password?</a>
                  </div>
                  <div class="text-center">
                    <a href="#">Create an account</a>
                  </div>
                </b-col>
              </b-row>
            </b-card>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    login: function () {
      asyncData();
    },
  },
  asyncData(context) {
    console.log(Object.keys(context));
    return axios
      .post("http://localhost:4000/user/sign-in", {
        'email': 'xuanhuy@gmail.com',
        'password': '11223344',
      })
      .then(function (res) {
        if (res.status != 200) {
          throw Error(res.status);
        }
        return res;
      })
      .then((data) => {
        console.log(data)
        //context.redirect("/");
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
.bg-primary {
  background-color: #4e73df;
  background-image: linear-gradient(200deg, #ab4de0 10%, #3922be 100%);
  background-size: cover;
}
.card {
  border: 0;
  padding: 0;
}
.card-body {
  padding: 0;
}
.bg-login-image {
  background-position: center;
  background-size: cover;
}
.form-control {
  border-radius: 2rem;
  padding: 1.5rem 1.5rem;
}
.btn {
  border-radius: 2rem;
  padding: 0.5rem;
}
.btn-facebook {
  background-color: #0a2988;
}
</style>