<template>
  <div id="2" class="container">
    <div class="form" name="form">
      <div class="input">
        <h3>Add User</h3>
        <hr />
        <b-form-group
          id="fieldset-1"
          label="Firstname"
          label-for="input-1"
          valid-feedback="Thank you!"
          :invalid-feedback="invalidFirstnameFeedback"
          :state="nameState"
        >
          <b-form-input
            id="input-1"
            type="text"
            v-model="name"
            :state="nameState"
            trim
          ></b-form-input>
        </b-form-group>
      </div>
      <div class="input">
        <b-form-group
          id="fieldset-2"
          label="Lastname"
          label-for="input-2"
          valid-feedback="Thank you!"
          :invalid-feedback="invalidLastnameFeedback"
          :state="lastnameState"
        >
          <b-form-input
            id="input-2"
            type="text"
            v-model="lastname"
            :state="lastnameState"
            trim
          ></b-form-input>
        </b-form-group>
      </div>
      <div class="input">
        <b-form-group
          id="fieldset-3"
          label="Age"
          label-for="input-3"
          valid-feedback="Thank you!"
          :invalid-feedback="invalidAgeFeedback"
          :state="ageState"
        >
          <b-form-input
            id="input-3"
            type="number"
            v-model="age"
            :state="ageState"
            trim
          ></b-form-input>
        </b-form-group>
      </div>
      <div class="d-grid gap-2">
        <button block class="button" @click="createUser()">Confirm</button>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import Vue from "vue";
import VueToastr from "vue-toastr";

Vue.use(VueToastr, {
  type: "success",
});
export default {
  name: "UserForm",

  computed: {
    nameState() {
      return this.name.length >= 4;
    },
    lastnameState() {
      return this.lastname.length >= 4;
    },
    ageState() {
      return this.age < 100 && this.age > 0;
    },
    invalidFirstnameFeedback() {
      if (this.name.length >= 4) {
        return "Enter at least 4 characters.";
      }
      return "Please enter something.";
    },
    invalidLastnameFeedback() {
      if (this.lastname.length >= 4) {
        return "Enter at least 4 characters.";
      }
      return "Please enter something.";
    },
    invalidAgeFeedback() {
      if (this.age < 100 && this.age > 0) {
        return "Please enter a real age.";
      }
      return "Please enter something.";
    },
  },
  data() {
    return {
      name: "",
      lastname: "",
      age: "",
    };
  },

  methods: {
    createUser() {
      if (this.name === "" || this.lastname === "" || this.age === "") {
        this.$toastr.defaultPosition = "toast-top-center";
        this.$toastr.defaultStyle = { "background-color": "red" };
        this.$toastr.s(
          "<font color='black'> Lütfen tüm alanları doldurun.</font>"
        );
        return false;
      }
      axios
        .post("https://dummyjson.com/users/add", {
          firstName: this.name,
          lastName: this.lastname,
          age: this.age,
        })
        .then((response) => {
          if (response.status === 200) {
            this.$toastr.defaultPosition = "toast-top-center";
            this.$toastr.defaultStyle = { "background-color": "green" };
            this.$toastr.s("<font color='black'> Başarılı</font>");
          }
        })
        .catch(() => {
          this.$toastr.defaultPosition = "toast-top-center";
          this.$toastr.defaultStyle = { "background-color": "red" };
          this.$toastr.s("<font color='black'> Bir sorun oluştu.</font>");
        });
    },
  },
};
</script>
<style>
.form {
  background-color: #ffff;
  padding: 1em;
  margin-bottom: 1em;
  width: 50%;
}
.input {
  text-align: justify;
  padding-top: 10px;
}
.container {
  width: 100%;
  background-color: #ffff;
  border-radius: 20px 20px 20px 20px;
}
hr {
  width: 200%;
  background-color: black;
  border-width: 3px 0 0 0;
  border-style: solid;
  height: 1px;
  opacity: 1 !important;
}
h3 {
  color: rgb(54, 19, 87);
}
.button {
  background-color: rgb(54, 19, 87);
  border-radius: 7px;
  border: 1px;
  height: 38px;
  color: #ffff;
}
.button:hover {
  opacity: 0.5;
}
</style>
