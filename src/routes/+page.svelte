<script>
	import JobAd from '../components/JobAd.svelte';
	import JobTag from '../components/JobTag.svelte';

	import logo from '/src/images/photosnap.svg';

	const ad = {
		company: 'Photosnap',
		logo: logo,
		isNew: true,
		isFeatured: true,
		position: 'Senior Frontend Developer',
		role: 'Frontend',
		level: 'Senior',
		postedAt: '1d ago',
		contract: 'Full Time',
		location: 'USA Only',
		languages: ['HTML', 'CSS', 'JavaScript']
	};
</script>

<svelte:head>
	<link rel="stylesheet" href="/src/css/app.css" />
	<link rel="stylesheet" href="/src/css/reset.css" />
</svelte:head>

<header class="header" />

<section class="content">
	<div class="tags">
		<div class="tags__container">
			<JobTag title={'HTML'} />
			<JobTag title={'CSS'} />
			<JobTag title={'JS'} />
		</div>

		<button class="tags__button">Clear</button>
	</div>

	<div class="ads">
		<JobAd {...ad} />
		<JobAd {...ad} />
		<JobAd {...ad} />
		<JobAd {...ad} />
	</div>
</section>

<style>
	/*
		//////////////////
		HEADER SECTION
		//////////////////
	*/

	.header {
		height: 156px;
		max-height: 156px;
		position: relative;
		background-color: var(--primary-color);
		background-image: url(../images/bg-header-desktop.svg);
	}

	/*
		//////////////////
		CONTENT SECTION
		//////////////////
	*/

	.content {
		margin: 0 2rem;
		/* max-width: 73rem; */
		flex-direction: column;
		/* padding: 0 2rem 2rem 2rem; */
	}

	@media only screen and (min-width: 769px) {
		
	}

	@media only screen and (min-width: 968px) {
		.content {
			margin: 0 auto;
			max-width: 96rem;
		}
	}

	/*
		//////////////////
		ADS SECTION
		//////////////////
	*/

	.ads {
		gap: 4rem;
		display: flex;
		flex-wrap: wrap;
	}

	
	@media only screen and (min-width: 680px) {
	}

	/*
		//////////////////
		TAGS
		//////////////////
	*/

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
</style>
