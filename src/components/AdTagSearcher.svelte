<script>
	import Select from 'svelte-select';

	export let tags = [];
	export let selectedTags = null;

	const groupBy = (item) => item.group;
</script>

<div class="tags">
	<div class="themed">
		<Select isMulti={true} {groupBy} items={tags} bind:value={selectedTags} />
	</div>
</div>

<style>
	.tags {
		position: relative;
		border-radius: 6px;
		padding: 1.5rem;
		background-color: var(--light-cyan-bg);
		top: -25px;
		margin-bottom: 2rem;
		box-shadow: var(--box-shadow);
	}

	.themed {
		--borderRadius: 8px;
		--borderFocusColor: #5ba4a4;
		--itemHoverColor: white;
		--itemHoverBG: var(--primary-color);
	}

	@media only screen and (min-width: 44em) {
		.tags {
			margin-bottom: 0;
		}
	}
</style>
