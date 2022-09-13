<script>
	import removeIcon from '/src/images/icon-remove.svg';

	export let title = 'default title';
</script>

<div class="tag">
	<span href="#" class="tag__title"> {title} </span>
	<button class="tag__button">
		<img class="tag__icon" src={removeIcon} alt="remove chip icon" />
	</button>
</div>

<style>
	.tag {
		display: flex;
		color: var(--primary-color);
	}

	.tag__title {
		margin-top: auto;
		margin-bottom: auto;
		font-size: 1rem;
		padding: 0px 6px;
		font-weight: 700;
		text-transform: uppercase;
		background-color: #f2f2f2;
		border-top-left-radius: 3px;
		border-bottom-left-radius: 3px;
		border: 1px solid var(--primary-color);
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
