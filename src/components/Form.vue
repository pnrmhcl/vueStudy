<template>
  <div id="1" class="container">
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
            type="text"
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
            type="text"
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
            type="number"
            v-model="age"
            :state="state"
            trim
          ></b-form-input>
        </b-form-group>
      </div>
      <div class="d-grid gap-2">
        <button block class="button">Confirm</button>
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
