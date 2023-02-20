<template>
  <div class="container">
    <div class="form">
      <div class="input">
        <h3>Add User</h3>
        <hr />
        <b-form-group
          id="fieldset-1"
          label="Firstname"
          label-for="input-1"
          valid-feedback="Thank you!"
          :invalid-feedback="invalidFeedback"
          :state="state"
        >
          <b-form-input
            id="input-1"
            v-model="name"
            :state="state"
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
          :invalid-feedback="invalidFeedback"
          :state="state"
        >
          <b-form-input
            id="input-2"
            v-model="lastname"
            :state="state"
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
          :invalid-feedback="invalidFeedback"
          :state="state"
        >
          <b-form-input
            id="input-3"
            v-model="age"
            :state="state"
            trim
          ></b-form-input>
        </b-form-group>
      </div>
      <div class="d-grid gap-2">
        <b-button block class="button" style="background-color: rgb(54, 19, 87)"
          >Confirm</b-button
        >
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "UserForm",
  computed: {
    state() {
      console.log(this);
      return this.name.length >= 4;
    },
    invalidFeedback() {
      if (this.name.length > 0) {
        return "Enter at least 4 characters.";
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
}
.container {
  width: 100%;
  background-color: #ffff;
  border-radius: 20px 20px 20px 20px;
}
hr {
  width: 200%;
  background-color: black;
}
h3 {
  color: rgb(54, 19, 87);
}
</style>
