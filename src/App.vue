<template>
  <div class="text-center">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Name</th>
          <th scope="col">Company</th>
          <th scope="col">Email</th>
          <th scope="col">Phone</th>
        </tr>
      </thead>
      <tbody v-for="user in users" :key="user.id">
        <tr>
          <th scope="row">{{ user.name }}</th>
          <td>{{ user.company.name}}</td>
          <td>{{user.email}}</td>
          <td>{{user.phone}}</td>
        </tr>
      </tbody>
    </table>

    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data: () => {
    return {
      users: []
    };
  },
  methods: {
    getUsers() {
      this.$axios
        .get("https://jsonplaceholder.typicode.com/users")
        .then(response => {
          this.users = response.data;
          console.log(this.users);
        });
    }
  },
  created() {
    this.getUsers();
  }
};
</script>

<style>
</style>