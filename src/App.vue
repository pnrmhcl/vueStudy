<template>
  <div id="app">
    <UserForm />
    <ListForm />
  </div>
</template>

<script>
import UserForm from "./components/Form.vue";
import ListForm from "./components/ListForm.vue";

export default {
  name: "App",
  components: {
    UserForm,
    ListForm,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
