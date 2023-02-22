<template>
  <div id="1" class="container">
    <div class="d-grid gap-2">
      <div class="listForm">
        <div class="input">
          <h3>User List</h3>
          <hr class="listHr" />
          <b-table striped hover :items="items"></b-table>
        </div>
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
.listHr {
  width: 100%;
  background-color: black;
  border-width: 1px 0 0 0;
  border-style: solid;
  height: 1px;
  opacity: 1 !important;
}
.listForm {
  background-color: #ffff;
  padding: 1em;
  margin-bottom: 1em;
  width: 100%;
}
</style>
