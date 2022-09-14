<script>
	import AdContainer from '../components/AdContainer.svelte';
	import AdTagSearcher from '../components/AdTagSearcher.svelte';

	import logo from '/src/images/photosnap.svg';

	const tags = ['Html', 'Css', 'Javascript'];

	const ads = [
		{
			logo: logo,
			company: 'Photosnap',
			position: 'Senior Frontend Developer',
			role: 'Frontend',
			level: 'Senior',
			postedAt: '1d ago',
			contract: 'Full Time',
			location: 'USA Only',
			languages: ['HTML', 'CSS', 'JavaScript'],
			isNew: true,
			isFeatured: true
		}
	];
</script>

<svelte:head>
	<link rel="stylesheet" href="/src/css/app.css" />
	<link rel="stylesheet" href="/src/css/reset.css" />
</svelte:head>

<header class="header" />

<section class="content">
	<AdTagSearcher {tags} />

	<AdContainer {ads} />
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
	}

	@media only screen and (min-width: 968px) {
		.content {
			margin: 0 auto;
			max-width: 96rem;
		}
	}
</style>
