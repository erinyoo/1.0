<script>
	let password = '';
	const hash = (s) =>
		s.split('').reduce((a, b) => {
			a = (a << 5) - a + b.charCodeAt(0);
			return a & a;
		}, 0);
	$: console.log(password, hash(password));

	import { blur } from 'svelte/transition';
	import cover from '$lib/growthpublisher/cover.png';
	import different from '$lib/growthpublisher/differentway.png';
	import posttypes from '$lib/growthpublisher/posttypes.png';
	import examples from '$lib/growthpublisher/examples.png';
	import sketch1 from '$lib/growthpublisher/sketch1.png';
	import sketch2 from '$lib/growthpublisher/sketch2.png';
	import stresstest from '$lib/growthpublisher/stresstest.png';
	import spec from '$lib/growthpublisher/spec.png';
	import flows from '$lib/growthpublisher/flows.png';
</script>

<div out:blur={{ delay: 100 }} in:blur={{ delay: 200 }} class="container">
	<div class="grid">
		<div class="title">
			<h1>Growing question posts</h1>
		</div>
		<img class="image" alt="The project cover" src={cover} />
		<div class="section">
			<h2>Overview</h2>
			<div class="description">
				In its simplest form Viva Answers is a platform for asking and answering questions. It's a
				place for employees to get answers through crowdsourced, conversational experiences. Viva
				Answers is still in it's nascent stages of life, and as a newer platform we're always
				looking for opportunities of growth. The goal was to find those opportunities while
				leveraging our existing parent platform, <a
					href="https://support.microsoft.com/en-us/topic/get-started-with-viva-engage-729f9fce-3aa6-4478-888c-a1543918c284"
					target={'_blank'}>Viva Engage</a
				>.
			</div>

			<h3><s>Discussion posts</s> Question posts</h3>
			<div class="description">
				To start off we analyzed how people are utilizing question posts and found some interesting
				behavior patterns. To give a little more context: in Viva Engage, people can utilize a
				variety of post types to help convey their thoughts: discussions, questions, polls, praises,
				and articles. In the experience, we default posts to discussions and (to no surprise) the
				majority of posts are discussion types.
			</div>
		</div>

		<img class="image" alt="Examples of misuse" src={examples} />
		<div class="section">
			<div class="description">
				As we performed our analysis we began to see a pattern of people asking questions in
				discussion post format rather than utilizing the question post.
			</div>
		</div>
	</div>

	{#if hash(password) === -1104066105}
		<div class="grid">
			<div class="section">
				<h2>The problem</h2>
				<div class="description">
					It's not entirely a surprise to us that this was happening. Our assumption was that this
					was due to the fact that our current flow requires users to open a dropdown menu to switch
					post types. Without knowing upfront, the UI provides no other signals to indicating to
					people that switching a post type is possible OR why it might be valuable for them.
				</div>
			</div>
			<img class="image" alt="The different post types" src={posttypes} />
		</div>

		<div class="grid">
			<div class="section">
				<h2>Is this a real problem?</h2>
				<div class="description">
					Why was this a problem though? So what if people were using discussions to post questions?
					Well for Viva Answers, this meant a loss in engagement; less questions being asked meant
					less knowledge we could leverage. This also meant there was an opportunity here for a
					quick and worthwhile growth investment.
				</div>
				<div class="description">
					In the point of view of the people asking questions, behind the scenes they weren't
					getting all the benefits a question post type provides. They were losing out on feature
					benefits such as upvoting capabilities and most importantly knowledge being properly
					indexed (i.e. getting their questions answered quickly).
				</div>
			</div>
		</div>

		<div class="grid">
			<div class="section">
				<h2>Finding a solution</h2>
				<div class="description">
					Before we dove into solving the problem, we set some ground rules or in other words,
					constraints and principles.
				</div>
			</div>

			<div class="notelayout">
				<div class="note">
					<div class="subheader">Rule 1</div>
					<div class="description">
						No AI, as much as AI would be a fantastic part of this solution we didn't have funding
						and needed to provide a solution that would work without it
					</div>
				</div>
				<div class="note">
					<div class="subheader">Rule 2</div>
					<div class="description">
						Keep it intuitive and non-disruptive, let's meet people where their at and keep
						disruption to a minimum
					</div>
				</div>
				<div class="note">
					<div class="subheader">Rule 3</div>
					<div class="description">
						Make it testable but also engineering feasible, we wanted a lightweight solution that
						didn't require much engineering lift and was easily A/B testable
					</div>
				</div>
			</div>

			<div class="section">
				<div class="description">And we also set up what success looked like for this project.</div>
			</div>

			<div class="notelayout">
				<div class="note">
					<div class="subheader">Metric 1</div>
					<div class="description">
						Increasing the number of question posts, with no negative impact on posts overall
					</div>
				</div>
				<div class="note">
					<div class="subheader">Metric 2</div>
					<div class="description">Increase in people using the question post type</div>
				</div>
			</div>
		</div>

		<div class="grid">
			<div class="section">
				<h2>Sketching and concepts</h2>
				<div class="description">We started off by sketching and brainstorming ideas.</div>
			</div>

			<img class="image" alt="Sketches" src={sketch1} />
			<img class="image" alt="Sketches" src={sketch2} />

			<div class="section">
				<h3>Narrowing in on a concept</h3>
				<div class="description">
					We narrowed our sketches and ideas down to three concepts and began to stress test. At
					this stage, we brought in engineering to help us look deeper into feasibility and
					testability.
				</div>
			</div>

			<img class="image" alt="Hi fidelity concepts" src={stresstest} />

			<div class="section">
				<div class="description">Even going as far as to look into other behavior paths.</div>
			</div>

			<img class="image" alt="Hi fidelity concepts" src={different} />
		</div>

		<div class="grid">
			<div class="section">
				<h2>The solution: a small teaching moment</h2>
				<div class="description">
					We landed on the concept of a small teaching moment. Based off engineering feedback, it
					was the most feasible and took the least amount of time which was an absolute plus for us.
					In addition, it was the most non-disruptive of our choices.
				</div>
			</div>

			<img class="image" alt="Spec" src={spec} />
			<img class="image" alt="User flows" src={flows} />
		</div>

		<div class="grid">
			<div class="section">
				<h2>Dogfooding and impact</h2>
				<div class="description">
					At Microsoft, dogfooding our products is one of the biggest parts of designing and
					creating features. This lightweight teaching moment was a perfect candidate for A/B
					testing.
				</div>

				<div class="description">
					We ran this experiment for two months in our inner ring and came out with some amazing
					results. Looking back at our success criteria we hit all marks:
				</div>
			</div>

			<div class="notelayout">
				<div class="note">
					<div class="subheader">Metric 1</div>
					<div class="description">
						Number of questions posts were increased at a statistically significant rate
					</div>
				</div>
				<div class="note">
					<div class="subheader">Metric 2</div>
					<div class="description">
						Number of users manually using the question post type was increased at a statistically
						significant rate
					</div>
				</div>
				<div class="note">
					<div class="subheader">Metric 3</div>
					<div class="description">
						There was even a bonus of an increase in search engagement related to questions
					</div>
				</div>
			</div>

			<div class="section">
				<div class="description">
					A rather successful mini-experiment! This data confirmed our assumptions and provided a
					path forward to bring this to production.
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

	a {
		text-decoration: none;
		color: $black;
		font-weight: 550;
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
