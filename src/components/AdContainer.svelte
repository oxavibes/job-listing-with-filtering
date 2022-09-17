<script>
	import Ad from './Ad.svelte';

	export let ads = [];
</script>

<div class="ads">
	{#each ads as ad}
		<Ad {...ad} />
	{/each}
</div>

<style>

	.ads {
		gap: 4.5rem;
		display: flex;
		flex-wrap: wrap;
	}

	@media only screen and (min-width: 44em) {
		.ads {
			gap: 2rem;
		}
	}
</style>
