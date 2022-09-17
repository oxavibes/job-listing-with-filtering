<script>
	import dayjs from 'dayjs';
	import relativeTime from 'dayjs/plugin/relativeTime';

	dayjs.extend(relativeTime);

	import AdTag from './AdTag.svelte';

	export let logo,
		company,
		position,
		role,
		level,
		updated,
		contract,
		location,
		isNew,
		isFeatured,
		languages,
		frameworks;
</script>

<div class="ad" class:ad__featured={isFeatured}>
	<img class="ad__logo" width="88" height="88" src={logo} alt="Company logo" />
	<div class="ad__details">
		<div class="ad__details-header">
			<span class="ad__company">{company}</span>
			{#if isNew}
				<span class="ad__chip ad__chip--new">New!</span>
			{/if}
			{#if isFeatured}
				<span class="ad__chip ad__chip--featured">Featured</span>
			{/if}
		</div>
		<h2>{position}</h2>
		<ul>
			<li>{dayjs().to(updated)}</li>
			<li>{contract}</li>
			<li>{location}</li>
		</ul>
	</div>
	<div class="ad__tags">
		<AdTag title={role} />
		<AdTag title={level} />

		{#each languages as language}
			<AdTag title={language} />
		{/each}

		{#each frameworks as framework}
			<AdTag title={framework} />
		{/each}
	</div>
</div>

<style>
	.ad {
		flex: 100%;
		background: white;
		border-radius: 6px;
		padding: 3.5rem 2rem 2rem 2rem;
		box-shadow: var(--box-shadow);
		position: relative;
		font-family: inherit;
	}

	.ad__featured {
		border-left: 5px solid var(--primary-color);
	}

	.ad__logo {
		position: absolute;
		width: 50px;
		height: 50px;
		top: -25px;
	}
	.ad__details {
		margin-bottom: 1.5rem;
		border-bottom: 1px solid #c1c3c2;
	}

	.ad__details-header {
		display: flex;
		align-items: center;
		margin-bottom: 10px;
	}

	.ad__details-header > :first-child {
		margin-right: 1rem;
	}

	.ad__details-header > :is(:last-child) {
		margin-left: 5px;
	}

	.ad__details h2 {
		color: var(--v-dark-grayish-cyan);
		margin-bottom: 0.6rem;
		font-size: 1.6rem;
	}

	.ad__details ul {
		padding: 0;
		margin-top: 0;
		display: inline-flex;
		list-style-position: inside;
	}
	.ad__details li {
		margin-right: 10px;
		font-family: inherit;
		font-size: 1.2rem;
		color: #929899;
	}

	.ad__details ul li:first-child {
		list-style-type: none;
	}

	.ad__chip {
		font-size: 1rem;
		color: white;
		padding: 4px 8px 2px 8px;
		font-weight: 700;
		display: inline-flex;
		border-radius: 12px;
		letter-spacing: 0.5px;
		text-transform: uppercase;
		background-color: transparent;
		box-shadow: var(--box-shadow);
	}

	.ad__chip--new {
		background-color: var(--primary-color);
	}

	.ad__chip--featured {
		background-color: black;
	}

	.ad__company {
		font-weight: 500;
		font-size: 1.6rem;
		display: inline-block;
		color: var(--primary-color);
	}

	.ad__tags {
		gap: 1rem;
		display: flex;
		flex-wrap: wrap;
		flex: 2;
	}

	@media only screen and (min-width: 44em) {
		.ad {
			padding: 2rem;
			display: flex;
			align-items: center;
		}
		.ad__logo {
			top: 0;
			width: 70px;
			height: 70px;
			position: relative;
			margin-right: 2rem;
		}

		.ad__details {
			border-bottom: 0;
		}

		.ad__details,
		.ad__details h2,
		.ad__details-header,
		.ad__details ul {
			margin-bottom: 3px;
		}

		.ad__tags {
			margin-left: auto;
			justify-content: flex-end;
		}
	}
</style>
