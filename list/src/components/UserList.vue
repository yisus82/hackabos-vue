<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        <User :user="user"></User>
      </li>
    </ul>
  </div>
</template>

<script>
import User from "./User";
export default {
  name: "UserList",
  props: {
    msg: String
  },
  components: {
    User
  },
  data() {
    return {
      users: []
    };
  },
  created() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(response => response.json())
      .then(json => (this.users = json));
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  list-style: none;
}
</style>
