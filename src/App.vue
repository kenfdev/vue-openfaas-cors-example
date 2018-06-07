<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
     AJAX Response: 
    </div>
    <div>
      {{ response }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      response: null
    };
  },
  created() {

    // const url = '/function/echo';
    const url = 'http://localhost:8080/function/echo';

    const data = {
      test: 'test'
    };
    fetch(url, {
      mode: 'cors',
      body: JSON.stringify(data),
      method: 'POST'
    }).then(res => res.json())
    .then(json => {
      this.response = json;
    });
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
