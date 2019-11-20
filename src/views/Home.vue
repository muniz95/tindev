<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/tindev.svg">
    <input type="text" name="username" id="username" v-model="username">
    <button @click="searchUsername()">Search</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'home',
  data: function () {
    return {
      username: ''
    }
  },
  methods: {
    searchUsername: async function () {
      const response = await axios.get(`https://api.github.com/users/${this.username}`)
      console.log(response.data)
    }
  }
}
</script>

<style lang="scss">
  .home {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-flow: column;
    @media (max-width: 640px) {
      width: 80%;
    }
    @media (min-width: 641px) and (max-width: 1023px) {
      width: 50%;
    }
    @media (min-width: 1024px) {
      width: 30%;
    }

    input, button {
      width: 100%;
    }
  }
</style>
