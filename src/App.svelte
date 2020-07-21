<script>
	import Header from './UI/Header.svelte'
	import MeetupGrid from './Meetups/MeetupGrid.svelte'
	import TextInput from './UI/TextInput.svelte'
	import Button from './UI/Button.svelte'

	let title = ''
	let subtitle = ''
	let address = ''
	let email = ''
	let imageUrl = ''
	let description = ''

	let meetups = [
		{
			id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup, we will have some experts that teach you how to code!',
			imageUrl: 'https://images.unsplash.com/photo-1516259762381-22954d7d3ad2?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2866&q=80',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'code@test.com'
		},
		{
			id: 'm2',
			title: 'Swim Together',
			subtitle: 'Let\'s go for some swimming',
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://images.unsplash.com/photo-1590674023830-9107e8f6e2ff?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2467&q=80',
			address: '27th Rooftop Ave, 32523 New York',
			contactEmail: 'swim@rooftop.com'
		}
	]

	function addMeetup() {
		const newMeetup = {
			id: Math.random().toString(),
			title,
			subtitle,
			description,
			imageUrl,
			address,
			contactEmail: email
		}

		meetups = [newMeetup, ...meetups]
	}
</script>

<Header />

<main>
	<form on:submit|preventDefault={addMeetup}>
		<TextInput
			id="title"
			label="Title"
			value={title}
			on:input={(event) => title = event.target.value} />
		<TextInput
			id="subtitle"
			label="Subtitle"
			value={subtitle}
			on:input={(event) => subtitle = event.target.value} />
		<TextInput
			id="address"
			label="Address"
			type="address"
			value={address}
			on:input={(event) => address = event.target.value} />
		<TextInput
			id="imageURL"
			label="Image URL"
			type="url"
			value={imageUrl}
			on:input={(event) => imageUrl = event.target.value} />
		<TextInput
			id="email"
			label="E-mail"
			type="email"
			value={email}
			on:input={(event) => email = event.target.value} />
		<TextInput
			id="description"
			label="Description"
			value={description}
			on:input={(event) => description = event.target.value}
			controlType="textarea"
			rows="3" />
		<Button type="submit" caption="Save" />
	</form>
	<MeetupGrid {meetups} />
</main>

<style>
	main {
		padding: 1em;
		margin: 0 auto;
	}

	form {
		width: 30rem;
		max-width: 90%;
		margin: auto;
	}
</style>