<script>
	let password = '';
	const hash = (s) =>
		s.split('').reduce((a, b) => {
			a = (a << 5) - a + b.charCodeAt(0);
			return a & a;
		}, 0);
	$: console.log(password, hash(password));
</script>

<nav>
	<a href="/">home</a>
	<a href="/about">about</a>
</nav>

<h1>about</h1>
<p>this is the about page</p>

{#if hash(password) === 1216985755}
	<p>you're in</p>
{:else}
	<div>
		<label for="password">Password:</label>
		<input id="password" bind:value={password} type="password" />
	</div>
{/if}

<style>
	div {
		font-family: sans-serif;
		font-size: 12px;
		margin-left: 50%;
		width: 400px;
		margin-top: 100px;
	}
	label {
		font-weight: bold;
	}
	input[type='password'] {
		width: 200px;
	}
</style>
