<script>
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	export let href;
	export let title;
	export let newTab = false;

	let currentPath;
	onMount(() => {
		currentPath = window.location.pathname;
	});
</script>

<a {href} class:active={$page.url.pathname == href} target={newTab ? '_blank' : ''}>{title}</a>

<style lang="scss">
	$font-family: inter, sans-serif;
	$font-weight: 500;

	a {
		font: $font-weight 1rem $font-family;
		color: black;
		text-transform: capitalize;
		text-decoration: none;
		transition: all 0.5s 0s ease;
	}

	.active {
		text-decoration: underline;
	}

	@media only screen and (max-width: 500px) {
		a {
			font: $font-weight 0.8rem $font-family;
			transition: all 0.5s 0s ease;
		}
	}

	@media only screen and (max-width: 400px) {
		a {
			font: $font-weight 0.6rem $font-family;
			transition: all 0.5s 0s ease;
		}
	}
</style>
