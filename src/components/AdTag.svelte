<script>
	import removeIcon from '/src/images/icon-remove.svg';

	export let title = 'default title';
</script>

<div class="tag">
	<span class="tag__title"> {title} </span>
</div>

<style>
	.tag {
		display: flex;
		overflow: hidden;
		border-radius: 2px;
		color: var(--primary-color);
		font-size: 1.2rem;
	}

	.tag__title {
		cursor: pointer;
		padding: 4px 9px;
		font-weight: 700;
		background-color: #f2f2f2;
		text-transform: capitalize;
		color: var(--primary-color);

		display: flex;
		align-items: center;
		justify-content: center;
	}

	.tag__title:hover {
		color: #f2f2f2;
		background-color: var(--primary-color);
	}
</style>
