<script>
	import AdTag from './AdTag.svelte';

	export let tags = [];
</script>

<div class="tags">
	<div class="tags__container">
		{#each tags as tag}
			<AdTag title={tag} closable />
		{/each}
	</div>

	<button class="tags__button">Clear</button>
</div>

<style>
	.tags {
		display: flex;
		position: relative;
		border-radius: 6px;
		padding: 1.5rem;
		box-shadow: var(--box-shadow);
		background-color: var(--light-cyan-bg);
		top: -25px;
		margin-bottom: 2rem;
	}

	.tags__container {
		display: flex;
		flex-wrap: wrap;
		margin-right: auto;
		gap: 0.5rem;
	}

	.tags__button {
		align-self: center;
		margin-left: 5px;
		background-color: transparent;
		color: var(--dark-grayish-cyan);
	}

	.tags__button:focus,
	.tags__button:hover {
		color: var(--primary-color);
		text-decoration: underline;
	}

	@media only screen and (min-width: 38em) {
		.tags {
			margin-bottom: 0;
		}
	}

	@media only screen and (min-width: 48em) {
		.tags__container {
			gap: 1rem;
		}
	}
</style>
