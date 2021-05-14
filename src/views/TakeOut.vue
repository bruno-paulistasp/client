<template>
<div class="container">
	<form @submit.prevent="submit">
		<h4> Retirar </h4>
		<div class="form-group col-md-3">
			<label for="amount"> Valor </label>

			<input type="text" class="form-control" name="amount" id="amount" v-model="form.amount">
		</div>

		<button type="submit" class="btn btn-primary"> Retirar </button>
	</form>
</div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'deposit',
  components: {
    //
  },

  data() {
	return {
		form: {
			amount: '',
		}
	}
  },

  methods: {
	...mapActions({
		takeout: 'auth/takeout'
	}),

	submit() {
		this.takeout(this.form).then(() => {
			this.$router.push({
				path: '/dashboard'
			})
		})
	}
  }
}
</script>
