<template>
	<div class="container">
		<app-header></app-header>
		<hr>
		<div class="row">
			<div class="col-xs-12 col-sm-6">
				<ul class="list-group">
					<app-server v-for="i in 5" :index="i"></app-server>
				</ul>
			</div>
			<app-server-info></app-server-info>
		</div>
		<hr>
		<app-footer></app-footer>
	</div>
</template>

<script>
	import Header from './components/Header.vue';
	import Footer from './components/Footer.vue';
	import Server from './components/Server.vue';
	import ServerInfo from './components/ServerInfo.vue';
	export default {
		components: {
			'app-header': Header,
			'app-footer': Footer,
			'app-server': Server,
			'app-server-info': ServerInfo
		}
	}
</script>

<style>
</style>