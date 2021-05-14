<template>
<div class=container>
	<ul class="nav">
		<li class="nav-item">
			<router-link class="nav-link"
				:to="{
					name: 'Home'
				}"
			>
				Home
			</router-link>
		</li>		
		<template v-if="authenticated">
			<li class="nav-item">
				<router-link class="nav-link"
					:to="{
						name: 'dashboard'
					}"
				>
					Dashboard
				</router-link>
			</li>
			<li class="nav-item">
				<router-link class="nav-link"
					:to="{
						name: 'deposit'
					}"
				>
					Depositar
				</router-link>
			</li>
			<li class="nav-item">
				<router-link class="nav-link"
					:to="{
						name: 'takeout'
					}"
				>
					Retirar
				</router-link>
			</li>
			<li class="nav-item">
				<a href="#" class="nav-link" @click.prevent="signOut">
					Sair
				</a>
			</li>
		</template>
		<template v-else>
			<li class="nav-item">
				<router-link class="nav-link"
					:to="{
						name: 'signin'
					}"
				>
					Logar
				</router-link>
			</li>
		</template>
	</ul>
</div>
</template>

<script>
	import { mapGetters, mapActions} from 'vuex'

	export default {
		computed: {
			...mapGetters({
				authenticated: 'auth/authenticated'
			})
		},

		methods: {
			...mapActions({
				signOutAction: 'auth/signOut'
			}),

			signOut() {
				this.signOutAction().then(() => {
					this.$router.replace({
						name: 'Home'
					})
				})
			}
		}
	}
</script>