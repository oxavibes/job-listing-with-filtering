<script>
	import removeIcon from '/src/images/icon-remove.svg';

	export let title = 'default title';
	export let closable = false;
</script>

<div class="tag">
	<span class="tag__title"> {title} </span>
	{#if closable}
		<button v-if="" class="tag__button">
			<img class="tag__icon" src={removeIcon} alt="remove chip icon" />
		</button>
	{/if}
</div>

<style>
	.tag {
		display: flex;
		overflow: hidden;
		border-radius: 2px;
		color: var(--primary-color);
	}

	.tag__title {
		display: flex;
		align-items: center;
		justify-content: center;

		font-size: 1rem;
		padding: 0px 6px;
		font-weight: 700;
		text-transform: uppercase;
		background-color: #f2f2f2;
		/* background-color: violet; */

		/* border: 1px solid var(--primary-color); */
	}

	.tag__button {
		border-top-right-radius: 3px;
		border-bottom-right-radius: 3px;

		background-color: var(--primary-color);
	}

	.tag__button:focus,
	.tag__button:hover {
		background-color: var(--v-dark-grayish-cyan);
	}

	.tag__icon {
		width: 7px;
		height: 7px;
	}
</style>
