<script>
	import { onMount } from 'svelte';
	import jobAds from '$lib/data/db.json';

	import AdContainer from '../components/AdContainer.svelte';
	import AdTagSearcher from '../components/AdTagSearcher.svelte';

	let ads = [];
	let tags = [];
	let roles = [];
	let levels = [];
	let languages = [];
	let frameworks = [];
	let selectedTags = null;

	//Computed properties equivalent in Vue.js
	$: filteredAds = selectedTags
		? ads.filter((ad) =>
				selectedTags.every((tag) => {
					if (tag.group == 'languages' || tag.group === 'frameworks') {
						return ad[tag.group].includes(tag.value);
					} else {
						return ad[tag.group] === tag.value;
					}
				})
		  )
		: ads;

	function extractAd(ad) {
		extractTags(ad);

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
			languages: ad.languages,
			frameworks: ad.frameworks
		};
	}

	function createSelectElements(arr, group) {
		return arr.map((item) => ({ value: item, label: item, group: group }));
	}

	function extractTags(ad) {
		roles = [...new Set([...roles, ad.role])];
		levels = [...new Set([...levels, ad.level])];
		languages = [...new Set([...languages, ...ad.languages])];
		frameworks = [...new Set([...frameworks, ...ad.frameworks])];
	}

	function formatTags() {
		return [
			...createSelectElements(roles, 'role'),
			...createSelectElements(levels, 'level'),
			...createSelectElements(languages, 'languages'),
			...createSelectElements(frameworks, 'frameworks')
		];
	}

	onMount(() => {
		ads = jobAds.map(extractAd);
		tags = formatTags();
	});
</script>

<svelte:head>
	<title>Front end Mentor - Job listing with filtering.</title>
</svelte:head>

<header class="header">
	<h1>Job listing with filtering</h1>
</header>
<main class="content">
	<AdTagSearcher bind:tags bind:selectedTags />

	<AdContainer ads={filteredAds} />
</main>

<style>
	.header {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 156px;
		max-height: 156px;
		position: relative;
		background-color: var(--primary-color);
		background-image: url(../images/bg-header-desktop.svg);
	}

	.header h1 {
		color: white;
		font-weight: 700;
		font-family: inherit;
		letter-spacing: 1px;
		visibility: hidden;
	}

	.content {
		margin: 0 2rem;
		flex-direction: column;
		padding-bottom: 2rem;
	}

	@media only screen and (min-width: 968px) {
		.content {
			margin: 0 auto;
			max-width: 968px;
		}
	}
</style>
