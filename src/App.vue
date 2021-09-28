<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>My 10 favourite Boolean email address boolean e-mail adress are:</h1>
    <ul>
      <li>
        <HelloWorld  v-for="(email,index) in randomEmail" :key="index" :email="email" />
      </li>
    </ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function () {
    return {
      randomEmail : [],
    }
  },
  methods: {

    /*async getEmail(n) {
      while (this.randomEmail.length < n) {
        let response = await axios.get('https://flynn.boolean.careers/exercises/api/random/mail');
        this.randomEmail.push(response.data.response);
        console.log(response.data.response)
      }
    },
    */
   
    getEmail(n) {
      for (let i = 0; i < n; i++) {
        axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
        .then((response) => {
          this.randomEmail.push(response.data.response);
          console.log(response.data.response);
          })
      }
    }

  },
  mounted() {
    console.log(axios);

    /**
     * axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
     * .then((response) => { this.randomEmail = response.data.response; });
     */

    this.getEmail(10);
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}

ul li {
  list-style-type: none;
}

</style>
