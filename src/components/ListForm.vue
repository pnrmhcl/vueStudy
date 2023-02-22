<template>
  <div id="1" class="container">
    <div class="d-grid gap-2">
      <div class="listForm">
        <div class="input">
          <h3>User List</h3>
          <hr class="listHr" />
          <nav class="navbar navbar-light bg-light">
            <input
              class="form-control mb-4"
              id="tableSearch"
              type="text"
              placeholder="Search.."
            />
          </nav>

          <b-table id="myTable" table hover :items="items"> </b-table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import $ from "jquery";

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
$(document).ready(function () {
  $("#tableSearch").on("keyup", function () {
    var value = $(this).val().toLowerCase();
    $("#myTable tr").filter(function () {
      $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1);
    });
  });
});

$(document).ready(function () {
  $("#listSearch").on("keyup", function () {
    var value = $(this).val().toLowerCase();
    $("#myList li").filter(function () {
      $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1);
    });
  });
});

$(document).ready(function () {
  $("#anythingSearch").on("keyup", function () {
    var value = $(this).val().toLowerCase();
    $("#myDIV *").filter(function () {
      $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1);
    });
  });
});
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
