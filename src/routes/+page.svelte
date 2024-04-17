<script lang="javascript">
	import { onMount } from 'svelte';
	import { blur } from 'svelte/transition';
	import suggested from '$lib/aisuggested/suggested.png';
	let ready = false;
	onMount(() => (ready = true));
	$: innerWidth = 0;
</script>

<svelte:head>
	<script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>
</svelte:head>

<svelte:window bind:innerWidth />

{#if ready}
	<div class="heading">
		<div out:blur={{ delay: 200 }} in:blur={{ delay: 1000 }}>
			<lottie-player
				src="https://lottie.host/0340c852-2a95-4549-9a21-fd15a8a8c39a/vTNBxS7KFv.json"
				background="transparent"
				speed="1"
				style="width: 175px;"
				direction="1"
				mode="normal"
				loop
				autoplay
			></lottie-player>
		</div>
		<div class="header">
			<h1 out:blur={{ delay: 200 }} in:blur={{ delay: 1650 }}>Hi! I'm Erin, a designer</h1>
			<div out:blur={{ delay: 1800 }} in:blur={{ delay: 1800 }} class="description">
				I’m a multi-disciplinary designer who is a curious crafter, passionate product thinker, and
				an addict for the aesthetics.
			</div>
		</div>
	</div>
{/if}

{#if ready}
	<div class="container">
		<div out:blur={{ delay: 200 }} in:blur={{ delay: 1900 }} class="grid">
			<div class="section">
				<a href="/aisuggested">
					<div class="card">
						<div class="cardheader">
							<div class="subheader">Microsoft Viva</div>
							<h3>Topics at a click of a button</h3>
						</div>
						<img class="image" alt="Introducing AI-suggested topics" src={suggested} />
					</div>
				</a>
			</div>
		</div>
	</div>
{/if}

<style lang="scss">
	$inter: inter, sans-serif;
	$gelica: gelica, sans-serif;
	$five-weight: 500;
	$black: #1e2019;
	$subtle: #9a9390;

	.container {
		margin: 124px auto;
	}

	.grid {
		display: grid;
		max-width: 1600px;
		width: 100%;
		grid-template-columns: repeat(25, 1fr);
	}

	.section {
		padding: 0 0 64px 0;
		grid-column-start: 8;
		grid-column-end: 19;
	}

	.subheader {
		color: $subtle;
		text-transform: uppercase;
		font: 1rem $inter;
		line-height: 175%;
	}

	.cardheader {
		display: flex;
		flex-direction: column;
		gap: 4px;
	}

	.card {
		border-radius: 15px;
		border: 1px solid #000;
		display: flex;
		flex-direction: column;
		padding: 48px 48px;
		gap: 32px;
		transition: all 200ms ease-in-out;
	}

	.card:hover {
		border-radius: 15px;
		border: 1px solid #000;
		box-shadow: -2px 4px 20px 0px rgba(123, 123, 123, 0.31);
		transition: all 200ms ease-in-out;
	}

	a {
		text-decoration: none;
		color: $black;
	}

	h3 {
		font: 1.6rem $gelica;
		margin: 0;
	}

	.description {
		font: 1rem $inter;
		color: $black;
		width: 65%;
		line-height: 1.8rem;
		margin: 0 auto;
		text-align: center;
	}

	h1 {
		text-align: center;
		font: 3.8rem $gelica;
		margin: 0px;
	}

	.heading {
		margin: 224px auto 72px auto;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 64px;
	}

	.header {
		display: flex;
		padding: 0 24px 0 24px;
		flex-direction: column;
		gap: 16px;
		z-index: 10;
	}

	@media only screen and (max-width: 700px) {
		h3 {
			font: 1rem $gelica;
			margin: 0;
		}

		.heading {
			margin: 224px auto 0px auto;
		}

		.container {
			margin: 48px auto;
		}
	}

	@media only screen and (max-width: 950px) {
	}

	@media only screen and (max-width: 800px) {
	}

	@media only screen and (max-width: 700px) {
	}
</style>
