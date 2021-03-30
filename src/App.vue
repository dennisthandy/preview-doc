<template>
	<h1>Issue Preview File Onpremis</h1>
	<DocPreview />
</template>

<script>
	import DocPreview from './components/DocPreview.vue';
	export default {
		components: {
			DocPreview,
		},
	};
	// This starter template is using Vue 3 experimental <script setup> SFCs
	// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
	*,
	*::before,
	*::after {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	body {
		position: relative;
		display: grid;
		place-items: center;
		min-height: 100vh;
		font-family: Arial, Helvetica, sans-serif;
	}
</style>
