<template>
  <div class="users">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="enter name" />
      <br />
      <input type="email" v-model="newUser.email" placeholder="enter email" />
      <br />
      <input type="submit" value="Add User" />
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted" />
        <span :class="{contacted: user.contacted}">
          {{ user.name }} : {{ user.email }}
        </span>
        <button v-on:click="deleteUser(user)">x</button>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Users',
    data() {
      return {
        newUser: {},
        users: [
          {
            name: 'John Doe',
            email: 'jdoe@gmail.com',
            contacted: true,
          },
          {
            name: 'Steve Smith',
            email: 'ssmith@gmail.com',
            contacted: false,
          },
          {
            name: 'Tom White',
            email: 'twhite@gmail.com',
            contacted: false,
          },
        ],
      };
    },
    methods: {
      addUser: function addUser(e) {
        e.preventDefault();
        this.users.push({
          name: this.newUser.name,
          email: this.newUser.email,
          contacted: false,
        });
        this.clearFields();
      },
      deleteUser: function deleteUser(user) {
        this.users.splice(this.users.indexOf(user), 1);
      },
      clearFields: function clear() {
        this.newUser.name = '';
        this.newUser.email = '';
      },
    },
    created() {
      this.$http.get('https://jsonplaceholder.typicode.com/users')
        .then((response) => {
          this.users = response.data;
        });
    },
  };
</script>

<style scoped>
  .contacted {
    text-decoration: line-through;
  }
</style>
