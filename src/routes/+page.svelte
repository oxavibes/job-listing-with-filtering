<script>
	import variables from '$lib/variables';
	import PocketBase from 'pocketbase';

	import AdContainer from '../components/AdContainer.svelte';
	import AdTagSearcher from '../components/AdTagSearcher.svelte';

	const client = new PocketBase(variables.pocketBaseClient);

	let page = 1;
	let perPage = 30;

	let tags = [];

	const extractAd = (ad) => {
		return {
			logo: ad.logo,
			company: ad.company,
			position: ad.position,
			role: ad.role,
			level: ad.level,
			contract: ad.contract,
			location: ad.location,
			isNew: ad.new,
			isFeatured: ad.featured,
			updated: ad.updated,
			languages: ad.languages.languages
		};
	};

	const getAds = async () => {
		try {
			const { items } = await client.records.getList('jobs', page, perPage);

			return items.map(extractAd);
		} catch (error) {
			throw new Error(error);
		}
	};
</script>

<svelte:head>
	<link rel="stylesheet" href="/src/css/app.css" />
	<link rel="stylesheet" href="/src/css/reset.css" />
</svelte:head>

<header class="header" />

<section class="content">
	<AdTagSearcher {tags} />

	{#await getAds()}
		<span>Waiting...</span>
	{:then ads}
		<AdContainer {ads} />
	{/await}
</section>

<style>
	.header {
		height: 156px;
		max-height: 156px;
		position: relative;
		background-color: var(--primary-color);
		background-image: url(../images/bg-header-desktop.svg);
	}
	.content {
		margin: 0 2rem;
		flex-direction: column;
		padding-bottom: 2rem;
	}

	@media only screen and (min-width: 968px) {
		.content {
			margin: 0 auto;
			max-width: 96rem;
		}
	}
</style>
