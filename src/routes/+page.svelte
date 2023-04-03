<script lang="ts">
	import { fly } from 'svelte/transition';

	import me from '$lib/assets/me.jpg';
	import rouxScreenshot from '$lib/assets/roux.png';

	let showProjects = true;
	let showExperience = false;
	let showContact = false;
	let name = '';
	let email = '';
	let message = '';
	let showInfoMessage = false;

	const handleSubmit = () => {
		showInfoMessage = true;
	};
</script>

<svelte:head>
	<style>
		body {
			font-family: 'Delius', sans-serif;
		}
	</style>
</svelte:head>

<nav class="navbar is-dark">
	<div class="navbar-brand">
		<a class="navbar-item" href="https://github.com/nickroberts217" target="_blank">
			<span class="icon"><i class="fa-brands fa-github" /></span>
		</a>
		<a class="navbar-item" href="https://medium.com/@nickroberts217" target="_blank">
			<span class="icon"><i class="fa-brands fa-medium" /></span>
		</a>
		<a class="navbar-item" href="https://www.linkedin.com/in/nick-roberts-b6b18992" target="_blank">
			<span class="icon"><i class="fa-brands fa-linkedin-in" /></span>
		</a>
	</div>
</nav>
<section class="section mb-6">
	<p class="title">Hello, I'm Nick.</p>
	<p class="subtitle">I develop secure, performant, and easy-to-use web applications.</p>
	<div class="tabs is-right">
		<ul>
			<li class:is-active={showProjects === true}>
				<a
					on:click={() => {
						showProjects = true;
						showExperience = false;
						showContact = false;
					}}>Projects</a
				>
			</li>
			<li class:is-active={showExperience === true}>
				<a
					on:click={() => {
						showProjects = false;
						showExperience = true;
						showContact = false;
					}}>Experience</a
				>
			</li>
			<li class:is-active={showContact === true}>
				<a
					on:click={() => {
						showProjects = false;
						showExperience = false;
						showContact = true;
					}}>Contact</a
				>
			</li>
		</ul>
	</div>
	{#if showProjects}
		<div class="columns is-multiline" in:fly={{ duration: 500 }}>
			<div class="column is-one-quarter">
				<div class="card">
					<div class="card-image">
						<figure class="image is-4by3">
							<a href="https://www.roux.nyc" target="_blank"><img src={rouxScreenshot} /></a>
						</figure>
					</div>
					<div class="card-content has-background-grey">
						<div class="content">
							<h4 class="has-text-white">Roux.nyc</h4>
							<div class="tags are-small">
								<span class="tag is-white is-rounded">Python</span>
								<span class="tag is-white is-rounded">Django REST Framework</span>
								<span class="tag is-white is-rounded">GCP</span>
								<span class="tag is-white is-rounded">PostgreSQL</span>
								<span class="tag is-white is-rounded">Docker</span>
								<span class="tag is-white is-rounded">Alpine.js</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	{/if}
	{#if showExperience}
		<article class="media mb-6" in:fly={{ duration: 500 }}>
			<figure class="media-left">
				<p class="image is-64x64">
					<img class="is-rounded" src={me} />
				</p>
			</figure>
			<div class="media-content">
				<div class="content">
					<p>
						In March I left <a href="https://www.joinforma.com" target="_blank">Forma</a>
						to pursue freelancing full time. For a limited time I am charging a lower-than-average hourly
						or fixed rate, dependent on technologies used. Please reach out to me on the next tab, or
						connect with me on LinkedIn. Thanks.
					</p>
				</div>
			</div>
		</article>
		<div class="columns" in:fly={{ duration: 500 }}>
			<div class="column is-4">
				<p class="subtitle has-text-info-dark">5+ yrs</p>
				<div class="tags are-small">
					<span class="tag is-info is-light is-rounded">Python</span>
					<span class="tag is-info is-light is-rounded">Django REST Framework</span>
					<span class="tag is-info is-light is-rounded">Django</span>
					<span class="tag is-info is-light is-rounded">PostgreSQL</span>
					<span class="tag is-info is-light is-rounded">Docker</span>
					<span class="tag is-info is-light is-rounded">Redis</span>
					<span class="tag is-info is-light is-rounded">HTML5</span>
					<span class="tag is-info is-light is-rounded">CSS3</span>
					<span class="tag is-info is-light is-rounded">Bootstrap</span>
				</div>
			</div>
			<div class="column is-4">
				<p class="subtitle has-text-warning-dark">2-4 yrs</p>
				<div class="tags are-small">
					<span class="tag is-warning is-light is-rounded">Google Cloud Platform</span>
					<span class="tag is-warning is-light is-rounded">MongoDB</span>
					<span class="tag is-warning is-light is-rounded">TypeScript</span>
					<span class="tag is-warning is-light is-rounded">Nest.js</span>
					<span class="tag is-warning is-light is-rounded">Alpine.js</span>
					<span class="tag is-warning is-light is-rounded">Bulma</span>
				</div>
			</div>
			<div class="column is-4">
				<p class="subtitle has-text-danger-dark">&lt; 1 yr</p>
				<div class="tags are-small">
					<span class="tag is-danger is-light is-rounded">K8s</span>
					<span class="tag is-danger is-light is-rounded">Svelte.js</span>
					<span class="tag is-danger is-light is-rounded">Tailwind CSS</span>
				</div>
			</div>
		</div>
	{/if}
	{#if showContact}
		{#if showInfoMessage}
			<div class="mb-5" in:fly={{ duration: 500 }}>
				<article class="message is-small is-info">
					<div class="message-body">
						Message was not sent, probably because the database is offline. Please connect with me
						on LinkedIn instead.
					</div>
				</article>
			</div>
		{/if}
		<form on:submit|preventDefault={handleSubmit} autocomplete="off" in:fly={{ duration: 500 }}>
			<div class="field is-horizontal">
				<div class="field-label is-normal">
					<label class="label">From</label>
				</div>
				<div class="field-body">
					<div class="field">
						<p class="control is-expanded has-icons-left">
							<input class="input" type="text" placeholder="Name" required bind:value={name} />
							<span class="icon is-small is-left">
								<i class="fa-regular fa-user" />
							</span>
						</p>
					</div>
					<div class="field">
						<p class="control is-expanded has-icons-left">
							<input class="input" type="email" placeholder="Email" required bind:value={email} />
							<span class="icon is-small is-left">
								<i class="fa-regular fa-envelope" />
							</span>
						</p>
					</div>
				</div>
			</div>
			<div class="field is-horizontal">
				<div class="field-label is-normal">
					<label class="label">How can I help?</label>
				</div>
				<div class="field-body">
					<div class="field">
						<div class="control">
							<textarea
								class="textarea"
								placeholder="Explain your project in depth"
								required
								bind:value={message}
							/>
						</div>
						<p class="help">
							What are you building? What are your requirements? Will this project be ongoing? Do
							you need designs?
						</p>
					</div>
				</div>
			</div>
			<div class="field is-horizontal">
				<div class="field-label">
					<!-- Left empty for spacing -->
				</div>
				<div class="field-body">
					<div class="field">
						<div class="control">
							<button class="button is-link"> Send message </button>
						</div>
					</div>
				</div>
			</div>
		</form>
	{/if}
</section>
<nav class="navbar is-light is-fixed-bottom">
	<div class="navbar-brand">
		<p class="navbar-item is-size-7">
			&copy; 2023&emsp;Built with&nbsp;
			<a href="https://kit.svelte.dev" target="_blank">SvelteKit</a>
		</p>
	</div>
</nav>
