<script>
	import { blur } from 'svelte/transition';
	import eevee from '$lib/assets/eevee.jpg';
	import flowers from '$lib/assets/flowers.jpg';
	import paint from '$lib/assets/paint.jpg';
</script>

<div out:blur={{ delay: 100 }} in:blur={{ delay: 200 }} class="container">
	<div class="grid">
		<div class="title">
			<h1>Hello! Nice to meet you.</h1>
		</div>

		<img class="eevee" alt="Eevee, my dog!" src={eevee} />
		<img class="erin" alt="Me in a flower field" src={flowers} />
		<img class="paint" alt="A painting I did" src={paint} />
	</div>

	<div class="grid" style="margin-top: 48px;">
		<div class="section">
			<div class="description">
				Hi there! Thanks for dropping by and taking the time to peruse. This website's still under a
				bit of construction, so please mind the dust!
			</div>

			<div class="description" style="margin-top: 32px;">
				As you may see, in my free time I love
				<b>CREATING</b>. Whether it's art, coding, or creating for the user, I am utterly in love
				with it. Other things I love are my dog, Eevee (pictured above) and of course being in
				fields of flowers.
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	$inter: inter, sans-serif;
	$gelica: gelica, sans-serif;
	$five-weight: 500;
	$black: #1e2019;
	$subtle: #9a9390;

	h1 {
		text-align: center;
		font: 4rem $gelica;
		font-weight: 400;
		margin: 0;
	}

	.eevee {
		border-radius: 15px;
		width: 100%;
		grid-column-start: 8;
		grid-column-end: 12;
	}

	.paint {
		border-radius: 15px;
		width: 100%;
		grid-column-start: 8;
		grid-column-end: 12;
	}

	.erin {
		border-radius: 15px;
		width: 100%;
		grid-column-start: 12;
		grid-column-end: 19;
	}

	.container {
		margin: 224px auto;
	}

	.title {
		grid-column-start: 4;
		grid-column-end: 23;
		margin: 0 0 64px 0;
	}

	.description {
		font: 1rem $inter;
		color: $black;
		line-height: 175%;
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
</style>
