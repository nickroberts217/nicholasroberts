<script lang="ts">
	import { fly } from 'svelte/transition';

	import me from '$lib/assets/me.jpg';
	import rouxScreenshot from '$lib/assets/roux.png';

	let showProjects = true;
	let showAbout = false;
	let showContact = false;
	let name = '';
	let email = '';
	let message = '';
	let showInfoMessage = false;

	const handleSubmit = () => {
		showInfoMessage = true;
	};
</script>

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
						showAbout = false;
						showContact = false;
					}}>Projects</a
				>
			</li>
			<li class:is-active={showAbout === true}>
				<a
					on:click={() => {
						showProjects = false;
						showAbout = true;
						showContact = false;
					}}>About</a
				>
			</li>
			<li class:is-active={showContact === true}>
				<a
					on:click={() => {
						showProjects = false;
						showAbout = false;
						showContact = true;
					}}>Contact</a
				>
			</li>
		</ul>
	</div>
	{#if showProjects}
		<div class="columns is-multiline" in:fly={{ duration: 500 }}>
			<div class="column is-one-third">
				<div class="card">
					<a class="card-image" href="https://www.roux.coffee" target="_blank">
						<figure class="image is-4by3">
							<img src={rouxScreenshot} />
						</figure>
						<div
							class="is-overlay py-2"
							style="bottom: auto; background-color: rgba(0, 0, 0, 0.5);"
						>
							<p class="subtitle has-text-centered has-text-white">Roux.coffee</p>
						</div>
						<div class="is-overlay p-2" style="top: auto; background-color: rgba(0, 0, 0, 0.5);">
							<div class="tags are-small">
								<span class="tag">Python</span>
								<span class="tag">Django REST Framework</span>
								<span class="tag">PostgreSQL</span>
								<span class="tag">Docker</span>
								<span class="tag">Google Places API</span>
								<span class="tag">Alpine.js</span>
							</div>
						</div>
					</a>
				</div>
			</div>
		</div>
	{/if}
	{#if showAbout}
		<article class="media mb-6" in:fly={{ duration: 500 }}>
			<figure class="media-left">
				<p class="image is-64x64">
					<img class="is-rounded" src={me} />
				</p>
			</figure>
			<div class="media-content">
				<div class="content">
					<p>
						Primarily backend, my favorite tech stack is Python-Django. My most recent position at <a
							href="https://www.joinforma.com"
							target="_blank">Forma</a
						> required me to learn Express.js so I've spent a couple of years in the Node.js world too.
						I like using frameworks to ease the development process, most notably Django REST Framework
						and Nest.js. I prefer them because they have built-in security, queueing, pagination, and
						other useful tools. Having previously worked for series B startups, I am well-versed in completing
						tasks within tight deadlines.
					</p>
					<p>
						When I'm not coding some of my hobbies include playing guitar, photography, brewing
						beer, and playing soccer. If you would like to get in touch, please contact me on the
						next tab or connect with me on <a
							href="https://www.linkedin.com/in/nick-roberts-b6b18992"
							target="_blank">LinkedIn</a
						>.
					</p>
				</div>
			</div>
		</article>
		<div class="columns" in:fly={{ duration: 500 }}>
			<div class="column is-4">
				<p class="subtitle has-text-info-dark">6+ yrs</p>
				<div class="tags are-small">
					<span class="tag is-info is-light">Python</span>
					<span class="tag is-info is-light">Django</span>
					<span class="tag is-info is-light">Django REST Framework</span>
					<span class="tag is-info is-light">PostgreSQL</span>
					<span class="tag is-info is-light">Celery</span>
					<span class="tag is-info is-light">Redis</span>
					<span class="tag is-info is-light">Docker</span>
					<span class="tag is-info is-light">Git</span>
					<span class="tag is-info is-light">Bootstrap</span>
				</div>
			</div>
			<div class="column is-4">
				<p class="subtitle has-text-warning-dark">2-4 yrs</p>
				<div class="tags are-small">
					<span class="tag is-warning is-light">Google Cloud Platform</span>
					<span class="tag is-warning is-light">TypeScript</span>
					<span class="tag is-warning is-light">Nest.js</span>
					<span class="tag is-warning is-light">Express.js</span>
					<span class="tag is-warning is-light">MongoDB</span>
					<span class="tag is-warning is-light">Bulma</span>
				</div>
			</div>
			<div class="column is-4">
				<p class="subtitle has-text-danger-dark">&lt; 1 yr</p>
				<div class="tags are-small">
					<span class="tag is-danger is-light">Svelte.js</span>
					<span class="tag is-danger is-light">K8s</span>
					<span class="tag is-danger is-light">Alpine.js</span>
					<span class="tag is-danger is-light">Tailwind CSS</span>
				</div>
			</div>
		</div>
	{/if}
	{#if showContact}
		{#if showInfoMessage}
			<div class="mb-5" in:fly={{ duration: 500 }}>
				<article class="message is-small is-info">
					<div class="message-body">
						Message was not sent, probably because the database is offline (Cloud SQL is
						expensive!). Please connect with me on <a
							href="https://www.linkedin.com/in/nick-roberts-b6b18992"
							target="_blank">LinkedIn</a
						> instead.
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
				<div class="field-label">
					<!-- Left empty for spacing -->
				</div>
				<div class="field-body">
					<div class="field">
						<div class="control">
							<textarea class="textarea" placeholder="Optional message" bind:value={message} />
						</div>
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
							<button class="button is-light">Send</button>
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
			&copy; 2023&ensp;Built with&nbsp;
			<a href="https://kit.svelte.dev" target="_blank">SvelteKit</a>
		</p>
	</div>
</nav>
