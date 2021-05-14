<template>
  <div class="container">
	Ag: {{ user.agency }} | C/C: {{ user.account }}
	<br><br>
    Ola {{ user.name }}
	<br>
	Saldo: R$ {{ user.balance }}
  </div>
</template>

<script>
	import { mapGetters} from 'vuex'

	export default {
		name: 'dashboard',
		
		computed: {
			...mapGetters({
				authenticated: 'auth/authenticated',
				user: 'auth/user',
			})
		},

		components: {
			//	
		}
	}
</script>
