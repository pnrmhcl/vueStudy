<template>
  <div id="1" class="container">
    <div class="d-grid gap-2">
      <div>
        <b-table striped hover :items="items"></b-table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      items: [],
      errors: [],
    };
  },

  created() {
    axios
      .get("https://dummyjson.com/users?select=age,firstName,lastName")
      .then((response) => {
        this.items = response.data.users;
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
<style>
.container {
  width: 100%;
  background-color: #ffff;
  border-radius: 20px 20px 20px 20px;
}
</style>
