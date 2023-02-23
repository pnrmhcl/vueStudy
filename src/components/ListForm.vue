<template>
  <div id="1" class="container">
    <div class="d-grid gap-2">
      <div class="listForm">
        <div class="input">
          <div style="display: flex">
            <h3>User List</h3>
            <div style="justify-content: space-between">
              <button type="button" v-show="simple" class="deleteButton">
                Delete
              </button>
            </div>
          </div>
          <hr class="listHr" />
          <nav class="navbar navbar-light bg-light">
            <input
              class="form-control mb-4"
              id="tableSearch"
              type="text"
              placeholder="Search.."
            />
          </nav>
          <div style="height: 350px; overflow-x: hidden; overflow-y: scroll">
            <b-table
              id="myTable"
              selectable
              select-mode="range"
              hover
              :items="items"
              @row-clicked="myRowClickHandler"
              ><template slot="preview" slot-scope="row">
                <b-form-checkbox
                  v-model="row.item.check"
                  @input="myRowClickHandler(row.record, row.index, row.item)"
                ></b-form-checkbox>
              </template>
              <template slot="fix" slot-scope="row">
                <b-form-checkbox v-model="row.item.fix"></b-form-checkbox>
              </template>
            </b-table>
          </div>
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
      simple: false,
    };
  },
  methods: {
    myRowClickHandler: function (record, index) {
      console.log(record, index + 1);
      console.log((this.simple = true));
    },
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
.deleteButton {
  position: absolute;
  right: 20em;
  background-color: rgb(54, 19, 87);
  border-radius: 7px;
  border: 1px;
  color: #ffff;
  width: 100px;
  height: 35px;
}
.deleteButton:hover {
  opacity: 0.5;
}
</style>
