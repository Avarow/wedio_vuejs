<template>
  <div id="app">
    <Login/>
  </div>
</template>

<script>
import Login from './components/Login.vue'

export default {
  name: 'app',
  components: {
    Login
  }
};
</script>

<style>

body{
  background-image: url("https://wedio-cdn-test.s3.eu-west-1.amazonaws.com/images/homepage/login/login_bg_x2.jpg");
  background-size: cover;
}

.w3-allerta {
  font-family: "Allerta Stencil", Sans-serif;
}

</style>
