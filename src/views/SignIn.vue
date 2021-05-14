<template>
<div class="container">
	<form @submit.prevent="submit">
		<div class="form-row ml-2">
			<div class="form-group col-md-1">
				<label for="agency">Agencia</label>

				<input type="text" class="form-control" name="agency" id="agency" v-model="form.agency" required>
			</div>

			<div class="form-group col-md-2">
				<label for="account">
					Conta
				</label>

				<input type="text" class="form-control" name="account" id="account" v-model="form.account" required>
			</div>
		</div>	

		<div class="form-group col-md-4">
			<label for="password">Password</label>

			<input type="password" class="form-control" name="password" id="password" v-model="form.password" required>
		</div>

		<button type="submit" class="btn btn-primary">Logar</button>
	</form>
</div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'signin',
  components: {
    //
  },

  data() {
	return {
		form: {
			email: '',
			password: '',
		}
	}
  },

  methods: {
	...mapActions({
		signIn: 'auth/signIn'
	}),

	submit() {
		this.signIn(this.form).then(() => {
			this.$router.replace({
				name: 'dashboard'
			})
		})
	}
  }
}
</script>
