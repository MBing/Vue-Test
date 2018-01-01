<template>
  <div class="test">
    <input v-model="title">
    <br />

    <h1>{{ title }}</h1>

    <p>{{ user.firstName }}</p>
    <p v-text="user.lastName"></p>
    <p v-if="isActive">This User is Active.</p>

    <ul>
      <li v-for="item in items">{{ item.title }}</li>
    </ul>

    <button v-on:click="greet(user.firstName)">Greeting</button>

    <br />

    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="pressEnter">
  </div>
</template>


<script>
  export default {
    name: 'Test',
    data() {
      return {
        title: 'Hello World',
        user: {
          firstName: 'John',
          lastName: 'Doe',
        },
        isActive: true,
        items: [
          {
            title: 'Item One',
          },
          {
            title: 'Item Two',
          },
          {
            title: 'Item Three',
          },
        ],
      };
    },
    methods: {
      greet: (userName) => {
        alert(`Hello ${userName}`);
      },
      pressKey: (e) => {
        console.log(e.target.value);
      },
      pressEnter: () => {
        console.log('You hit enter!');
      },
    },
  };
</script>

<style scoped>

</style>
