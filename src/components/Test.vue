<template>
  <div class="test">
    <h1>{{ title }}</h1>
    <p>{{ user.firstName }}</p>
    <p v-text="user.lastName"></p>
    <p v-if="isActive">This User is Active.</p>
    <ul>
      <li v-for="item in items">{{ item.title }}</li>
    </ul>
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
  };
</script>

<style scoped>

</style>
