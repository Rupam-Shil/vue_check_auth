<template>
	<div class="register">
		<h1>Register</h1>
		<form @submit.prevent="register">
			<input v-model="email" type="email" placeholder="Email" />
			<input v-model="password" type="password" placeholder="Password" />
			<input type="submit" value="register" />
			<p>
				Already have an account?<router-link to="/login">Login Now</router-link>
			</p>
		</form>
	</div>
</template>

<script>
import firebase from 'firebase';
import { ref } from 'vue';
export default {
	setup() {
		const email = ref('');
		const password = ref('');

		const register = () => {
			firebase
				.auth()
				.createUserWithEmailAndPassword(email.value, password.value)
				.then((user) => {
					alert(user);
				})
				.catch((err) => alert(err.message));
		};
		return { email, password, register };
	},
};
</script>
