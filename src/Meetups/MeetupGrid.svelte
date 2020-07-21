<script>
	import MeetupItem from './MeetupItem.svelte'

	export let meetups
</script>

<section>
	{#each meetups as meetup (meetup.id)}
		<MeetupItem {...meetup} />
	{/each}
</section>

<style>
	section {
		width: 100%;
		display: grid;
		grid-template-columns: 1fr;
		gap: 2rem;
		padding: 1rem;
	}

	@media (min-width: 768px) {
		section {
			grid-template-columns: repeat(2, 1fr);
			padding: 2rem 3vw;
		}
	}
</style>