<script lang="ts">
	import { onMount } from 'svelte';

	let now = new Date();
	let options = [
		'Allison',
		'Anastasia',
		'Brendan',
		'Celeste',
		'Cole',
		'Connor',
		'Corey',
		'Ella',
		'Grace',
		'Kevin',
		'Luke',
		'Nick',
		'Yael',
	];
	let excluded = [];
	let goalies = [];
	let needed = 2;

	const addToExcluded = async (index) => {
		const option = options[index];
		excluded.push(option);
		excluded = excluded.sort();
		options.splice(index, 1);
		options = options;
	};

	const removeFromExcluded = async (index) => {
		const exclude = excluded[index];
		options.push(exclude);
		options = options.sort();
		excluded.splice(index, 1);
		excluded = excluded;
	};

	const runGen = async (amount) => {
		const optionsCopy = [...options];
  		for (let i = optionsCopy.length - 1; i > 0; i--) {
    			const j = Math.floor(Math.random() * (i + 1));
    			const temp = optionsCopy[i];
    			optionsCopy[i] = optionsCopy[j];
    			optionsCopy[j] = temp;
  		}
		goalies = [optionsCopy[0], optionsCopy[1]];

	};
</script>

<section class="hero">
	<div class="hero-body pb-1">
		<h1 class="title is-1">GoalieGen&trade; by C2C</h1>
		<h4 class="subtitle is-6">{now.toDateString()}</h4>
  	</div>
	<div class="hero-body">
		<h4 class="subtitle is-4">Team Members</h4>
		<div class="tags">
			{#each options as option, index (index)}
			<span class="tag is-medium" on:click={() => addToExcluded(index)}>
				{option}
				<button class="delete is-small"></button>
			</span>
			{/each}
		</div>
		<br>
		<h4 class="subtitle is-4">Absent</h4>
		{#if excluded.length > 0}
			<div class="tags">
				{#each excluded as exclude, index (index)}
				<span class="tag is-medium is-danger" on:click={() => removeFromExcluded(index)}>
					{exclude}
					<button class="delete is-small"></button>
				</span>
				{/each}
			</div>
		{:else}
		<div class="tags">No one</div>
		{/if}
		<br>
		<h4 class="subtitle is-4">Number of goalies needed</h4>
		<form on:submit|preventDefault={runGen} autocomplete="off">
			<div class="field is-grouped">
				<div class="control is-expanded">
					
					<input class="input" type="number" required bind:value={needed} />
				</div>
				<div class="control">
					<button class="button is-rounded" type="submit">Run</button>
				</div>
			</div>
		</form>
		<br>
		{#if goalies.length > 0 && needed === 2}
		<p>Goalies: {goalies.join(', ')}</p>
		{:else if goalies.length > 0 && needed === 1}
		<p>Goalies: {goalies[0]}</p>
		{/if}
	</div>
</section>
<section class="hero">
	<div class="hero-body mt-4">
		<p class="is-size-7">&copy; 2024</p>
	</div>
</section>
