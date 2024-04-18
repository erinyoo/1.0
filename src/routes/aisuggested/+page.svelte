<script>
	let password = '';
	const hash = (s) =>
		s.split('').reduce((a, b) => {
			a = (a << 5) - a + b.charCodeAt(0);
			return a & a;
		}, 0);
	$: console.log(password, hash(password));

	import { blur } from 'svelte/transition';
	import cover from '$lib/aisuggested/cover.png';
	import topicbar from '$lib/aisuggested/topicbar.png';
	import showcase from '$lib/aisuggested/showcase.png';
	import guidelines from '$lib/aisuggested/guidelines.png';
	import distinction from '$lib/aisuggested/visual.png';
	import iterations from '$lib/aisuggested/iterations.png';
</script>

<div out:blur={{ delay: 100 }} in:blur={{ delay: 200 }} class="container">
	<div class="grid">
		<div class="title">
			<h1>Topics at your fingertips</h1>
		</div>
		<img class="image" alt="The project cover" src={cover} />
		<div class="section">
			<h2>Overview</h2>
			<div class="description">
				In its simplest form Viva Answers is a platform for asking and answering questions. It's a
				place for employees to get answers through crowdsourced, conversational experiences. I was
				tasked with solving a high area of friction within our question publishing experience:
				adding topics.
			</div>
			<h3>Topics and the topics bar</h3>
			<div class="description">
				Topics are a required part of questions in Viva Answers. As a required step within the
				publishing flow it was one of the main reasons users abandoned questions.
			</div>
		</div>
		<img class="image" alt="AI topics bar" src={topicbar} />
		<div class="section">
			<div class="description">
				At first glance, the small bar of white space seems simple and innocent. To our surprise, it
				was one of the main reasons users abandoned asking their questions. This meant less
				questions were being asked and in turn less knowledge was being shared.
			</div>
		</div>
	</div>

	{#if hash(password) === -1104066105}
		<div class="grid">
			<div class="section">
				<h2>Understanding the problem</h2>
				<div class="description">
					We performed interviews to further understand how people were interacting with the topic
					bar. It revealed some interesting insights as to why people were actually struggling:
				</div>
			</div>

			<div class="notelayout">
				<div class="note">
					<div class="subheader">Insight 1</div>
					<div class="description">
						People didn’t immediately recognize the topics bar as a search bar
					</div>
				</div>
				<div class="note">
					<div class="subheader">Insight 2</div>
					<div class="description">
						People didn’t immediately recognize the topics bar as a search bar
					</div>
				</div>
				<div class="note">
					<div class="subheader">Insight 3</div>
					<div class="description">
						People didn’t immediately recognize the topics bar as a search bar
					</div>
				</div>
			</div>
			<div class="section">
				<div class="description">
					We realized that the topic picking experience was quite a huge undertaking. For such a
					small feature, it weighed heavily on the entire process of asking a question <i
						>especially because it was a required step.</i
					> The asking experience should be easy, not difficult.
				</div>
			</div>
		</div>

		<div class="grid">
			<div class="section">
				<h2>Reframing the problem</h2>
				<div class="description">
					Due to engineering constraints and previous design constraints, the process of adding a
					topic had become arduous for people. To help us think through possible solutions, we posed
					a question to help reframe our problem: how might we make it as easy as possible for
					people to attach topics to their questions?
				</div>
			</div>
		</div>

		<div class="grid">
			<div class="section">
				<h2>Introducing: AI-suggested Topics</h2>
			</div>
			<img class="image" alt="Introducing AI-suggested topics" src={showcase} />
			<div class="section">
				<div class="description">
					AI-suggested topics makes adding topics as simple as the click of a button. Compose your
					question, and behind the scenes AI will process your content and surface suggested topics
					for you to choose, all you have to do is click.
				</div>
			</div>
		</div>

		<div class="grid">
			<div class="section">
				<h2>The nitty gritty</h2>
				<div class="description">
					Before we landed on our final shipped feature, the solution went through it's fair share
					of iterations before reaching it's final stage.
				</div>
				<h3>AI in Microsoft</h3>
				<div class="description">
					As one of the first AI features being released on the Viva Engage platform, we had to
					familiarize ourselves with evolving company guidelines and designs on AI and Copilot.
				</div>
			</div>

			<img class="image" alt="Microsoft's AI design guidelines" src={guidelines} />

			<div class="section">
				<h3>Being intentional</h3>
				<div class="description">
					It also meant thinking about language and visual distinctions. In addition to suggesting
					existing topics, the AI will create new topics for users and recommend them, this is when
					the AI *generates* a topic. The distinction may not be important to users, but guidelines
					state our design had to visually distinguish these topics to be as explicit as possible.
				</div>
			</div>

			<img class="image" alt="Visual distinction" src={distinction} />

			<div class="section">
				<h3>Embracing iterations</h3>
				<div class="description">
					Then came the part of gathering feedback on our high level concepts from the bigger design
					and engineering team to break down our concepts to feasible, scalable, and testable
					designs.
				</div>
			</div>

			<img class="image" alt="Visual distinction" src={iterations} />
		</div>

		<div class="grid">
			<div class="section">
				<h2>The impact</h2>
			</div>
			<div class="notelayout">
				<div class="note">
					<div class="subheader">Impact 1</div>
					<div class="description">
						<b><h3>54%</h3></b> Topics added are suggested topics
					</div>
				</div>
				<div class="note">
					<div class="subheader">Impact 2</div>
					<div class="description"><b><h3>Overall</h3></b> Decrease in question abandonment</div>
				</div>
			</div>
		</div>

		<div class="grid">
			<div class="section">
				<h2>Growing pains</h2>
				<div class="description">
					As a first project the learnings and takeaways were invaluable. As a developer turned
					designer my mindset shift has been one of the hardest parts of growing as a designer. Some
					key points I felt worthy of noting:
				</div>
				<div class="description">
					<ul>
						<li>
							<b>Sketch!</b> Creating hi-fidelity concepts early seems tempting, but it's a trap. To
							be able to effectively gain buy-in from stakeholders early on in the process, sketches
							are one of the most powerful ways to do so. If not sketches, then lo-fidelity mocks.
						</li>
						<li>
							<b>Communicate often and early</b> Communication is truly key when working with cross-functional
							teams. Oversharing never seemed to be a problem.
						</li>
						<li>
							<b>Get feedback often and early.</b> Obviously too much feedback can be a recipe for "too
							many cooks in the kitchen", but tweaking the spacing between two components for 30 minutes
							will also get you nowhere.
						</li>
						<li>
							<b>Problem understanding is key.</b> Without a well-defined problem or even an understanding
							of your problem, it'll be difficult to ideate or even create proper solutions. Taking time
							to truly define and gather information surrounding the problem can set a project up for
							success.
						</li>
					</ul>
				</div>
			</div>
		</div>
	{:else}
		<div class="grid">
			<div class="enterpassword">
				<h3>The full case study is under NDA</h3>
				<div class="inputlabel">
					<label for="password">To see more, please enter password</label>
					<input id="password" bind:value={password} type="password" />
				</div>
			</div>
		</div>
	{/if}
</div>

<style lang="scss">
	$inter: inter, sans-serif;
	$gelica: gelica, sans-serif;
	$five-weight: 500;
	$black: #1e2019;
	$subtle: #9a9390;

	label {
		font: 1rem $inter;
		color: $black;
		line-height: 175%;
	}

	input[type='password'] {
		width: 100%;
		height: 32px;
		background-color: rgba(183, 167, 162, 0.05);
		border-radius: 8px;
		border: 1px solid $black;
		font: 1rem $inter;
		color: $black;
		line-height: 175%;
		padding: 0 8px 0 8px;
	}

	h1 {
		text-align: center;
		font: 4rem $gelica;
		font-weight: 400;
		margin: 0;
	}

	h2 {
		font: 2.5rem $gelica;
		margin: 0 0 8px 0;
	}

	h3 {
		font: 1.6rem $gelica;
		margin: 24px 0 8px 0;
	}

	.inputlabel {
		display: flex;
		flex-direction: column;
		gap: 8px;
	}

	.enterpassword {
		grid-column-start: 8;
		grid-column-end: 19;
		display: flex;
		flex-direction: column;
		gap: 12px;
	}

	.subheader {
		color: $subtle;
		text-transform: uppercase;
		font: 1rem $inter;
		line-height: 175%;
	}

	.notelayout {
		display: flex;
		justify-content: space-between;
		gap: 32px;
		grid-column-start: 6;
		grid-column-end: 21;
		margin: 0 0 64px 0;
	}

	.note {
		flex-grow: 1;
		display: flex;
		padding: 24px 32px 48px 32px;
		flex-direction: column;
		align-items: flex-start;
		gap: 12px;
		border-radius: 8px;
		border: 1px solid $black;
		box-shadow: 2px 2px 8px 0px rgba(183, 167, 162, 0.43);
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

	.image {
		margin: 0 0 64px 0;
		width: 100%;
		grid-column-start: 6;
		grid-column-end: 21;
		border-radius: 15px;
		box-shadow: -1px 4px 10px 0px rgba(135, 138, 143, 0.2);
	}

	@media only screen and (max-width: 700px) {
		.image {
			margin: 0 0 64px 0;
			grid-column-start: 4;
			grid-column-end: 23;
		}

		.section {
			padding: 0 0 64px 0;
			grid-column-start: 4;
			grid-column-end: 23;
		}

		.enterpassword {
			grid-column-start: 4;
			grid-column-end: 23;
			display: flex;
			flex-direction: column;
			gap: 12px;
		}

		h1 {
			text-align: center;
			font: 3rem $gelica;
			font-weight: 400;
			margin: 0;
		}

		h2 {
			font: 1.6rem $gelica;
			margin: 0 0 8px 0;
		}

		h3 {
			font: 1.2rem $gelica;
			margin: 24px 0 8px 0;
		}

		.container {
			margin: 164px auto;
		}
	}
</style>
