<template>
  <div class="login w3-display-bottomright w3-allerta w3-large">
  	<p> {{title}} </p>
  	<p> {{descr}} </p>
  	<form v-if="!register" id="loginForm" @submit="checkForm">
  		<p class="errorMessage" v-if="emailError.length"> {{emailError}} </p>
  		<p>
  			<label for="email"> {{email}} </label>
  			<input type="email" name="email" v-model="emailTyped">
  		</p>

  		<p class="errorMessage" v-if="passwordError.length"> {{passwordError}} </p>
  		<p>
  			<label for="password"> {{password}} </label>
  			<input type="password" name="password" v-model="passwordTyped">
  		</p>
  		<p>
    		<input class="w3-button w3-aqua w3-round-xxlarge" type="submit" value="Sign In">  
  		</p>
  	</form>
  	<button class="w3-button w3-white w3-round-xxlarge" v-if="!register" v-on:click="switchForm"> Register </button>

  	<form v-if="register" id="RegisterForm" @submit="checkForm">
  		<p class="errorMessage" v-if="emailError.length"> {{emailError}} </p>
  		<p>
  			<label for="email"> {{email}} </label>
  			<input type="email" name="email" v-model="emailTyped">
  		</p>

		<p  class="errorMessage" v-if="usernameError.length"> {{usernameError}} </p>
  		<p>
  			<label for="username"> {{username}} </label>
  			<input type="text" name="username" v-model="usernameTyped">
  		</p>

  		<p  class="errorMessage" v-if="passwordError.length"> {{passwordError}} </p>
  		<p>
  			<label for="password"> {{password}} </label>
  			<input type="password" name="password" v-model="passwordTyped">
  		</p>
  		<p>
    		<input class="w3-button w3-aqua w3-round-xxlarge" type="submit" value="Register">  
  		</p>
  	</form>
  	<button class="w3-button w3-white w3-round-xxlarge" v-if="register" v-on:click="switchForm"> Sign In </button>
  	<div class="fb-login-button" data-width="auto" data-size="large" data-button-type="login_with" data-auto-logout-link="false" data-use-continue-as="false"></div>

  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
  	return {
    	title : 'WELCOME to Wedio —', 
    	descr : 'the fastest-growing European community of creators',
    	email : 'Email',
    	password : 'Password',
    	username : 'Username',
    	emailTyped : '',
    	emailError : '',
    	passwordTyped : '',
    	passwordError : '',
    	usernameTyped : '',
    	usernameError : '',
    	register : false
    }
  },
  methods:{
  	checkForm:function(e){
  		this.resetErrors();
  		if(!this.emailTyped)
  			this.emailError = "Email required";
  		else{
  			var pattern = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      		if(!pattern.test(this.emailTyped))
      			this.emailError = "The email address you supplied is invalid";
  			}
  		if(!this.passwordTyped)
  			this.passwordError = "Password required";

  		if(this.register === true){
  			if(!this.usernameTyped){
  				this.usernameError = "Username required";
  			}
  		}
  		e.preventDefault();
  	},

  	resetErrors:function(){
  		this.emailError='';
  		this.passwordError='';
  		this.usernameError='';
  	},

  	switchForm:function(){
  		this.resetErrors();
  		if(this.register === true)
  			this.register = false;
  		else
  			this.register = true;
  	}
  }
};
</script>

<style scoped>

.login{
	height: 60%;
	width: 70%;
}

p{
	color: white;
}

.errorMessage{
	color: red;
}

</style>