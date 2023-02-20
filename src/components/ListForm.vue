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
export default {
  data() {
    return {
      items: [
        { age: 40, first_name: "Dickerson", last_name: "Macdonald" },
        { age: 21, first_name: "Larsen", last_name: "Shaw" },
        { age: 89, first_name: "Geneva", last_name: "Wilson" },
        { age: 38, first_name: "Jami", last_name: "Carney" },
      ],
    };
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
