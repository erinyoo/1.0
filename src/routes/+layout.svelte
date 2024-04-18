<script>
	import NavLink from '$lib/components/NavLink.svelte';

	import { onMount } from 'svelte';

	let ready = false;
	onMount(() => (ready = true));

	function copyClipboard() {
		navigator.clipboard.writeText('erinswyoo@gmail.com');
	}
</script>

{#if ready}
	<nav>
		<div class="navlinks">
			<NavLink href="/" title="Home" />
			<NavLink href="/about" title="About" />
			<NavLink href="mailto:erinswyoo@gmail.com" title="Contact" />
			<NavLink
				href="https://docs.google.com/document/d/1yQS4ySt_lm7bJz4PTk1lBg_E-WFynAwQ0ElxqZ2J97c/edit?usp=sharing"
				title="Resume"
				newTab={true}
			/>
		</div>
	</nav>
{/if}

<slot />

<footer>
	{#if ready}
		<div class="subheader">Get in touch</div>

		<div class="footerlinks">
			<div class="linkitem"><a href="https://github.com/erinyoo" target="_blank">Github</a></div>
			<div class="linkitem">
				<a href="https://www.linkedin.com/in/erinyoo" target="_blank">Linkedin</a>
			</div>
			<button on:click={copyClipboard} class="linkitem">Copy my email: hello@erinyoo.com</button>
		</div>

		<div class="copyright">© 2024 Erin Yoo</div>
	{/if}
</footer>

<style lang="scss">
	$inter: inter, sans-serif;
	$gelica: gelica, sans-serif;
	$font-weight: 500;
	$lightWhite: #fafafa;
	$black: #1e2019;
	$subtle: #9a9390;

	:global(body) {
		background-color: $lightWhite;
		margin: 0;
		min-height: 100vh;
		display: flex;
		flex-direction: column;
	}

	a {
		text-decoration: none;
		color: $black;
	}

	button {
		border: 0;
		background-color: $lightWhite;
		padding: 0;
	}

	button:hover {
		cursor: pointer;
	}

	footer {
		margin-top: auto;
		height: 400px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 24px;
	}

	nav {
		position: fixed;
		display: flex;
		width: 100%;
		justify-content: center;
		align-items: center;
		border-bottom: 1px solid $black;
		background-color: $lightWhite;
		z-index: 100;
	}

	.subheader {
		color: $subtle;
		text-transform: uppercase;
		font: 1rem $inter;
		line-height: 175%;
	}

	.copyright {
		font: 1rem $gelica;
		line-height: 175%;
		color: $subtle;
		font-weight: 200;
	}

	.linkitem {
		font: 500 1rem $inter;
		display: flex;
		align-items: center;
		gap: 8px;
	}

	.footerlinks {
		display: flex;
		width: 100%;
		justify-content: center;
		align-items: center;
		gap: 24px;
		margin-top: 0;
	}

	.navlinks {
		display: flex;
		padding: 32px 64px;
		align-items: flex-start;
		gap: 24px;
		transition: all 0.5s 0s ease;
	}

	@media only screen and (max-width: 700px) {
		.navlinks {
			padding: 32px 64px;
			gap: 16px;
			transition: all 0.5s 0s ease;
		}

		.footerlinks {
			flex-direction: column;
		}
	}
</style>
