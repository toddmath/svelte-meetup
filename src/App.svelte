<script>
	import ContactCard from './ContactCard.svelte'

	let age = 34;
	let name = 'Todd';
	let description = 'A short description'
	let jobTitle = 'Full stack developer'
	let imageSrc = 'https://images.unsplash.com/photo-1504401774599-1b5378bfaae3?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1348&q=80'
	let formState = 'empty';

	let createdContacts = []

	$: uppercaseName = name.toUpperCase()

	function incrementAge() {
		age += 1
	}

	function addContact() {
		if (
			name.trim().length == 0
			|| jobTitle.trim().length == 0
			|| imageSrc.trim().length == 0
			|| description.trim().length == 0
			) {
			formState = 'invalid'
			return
	}

		formState = 'done'
		createdContacts = [
			...createdContacts,
			{
				id: Math.random(),
				name,
				jobTitle,
				imageUrl: imageSrc,
				desc: description
			}
		]
 }

 function deleteFirst() {
		createdContacts = createdContacts.slice(1)
 }

 function deleteLast() {
		createdContacts = createdContacts.slice(0, -1)
 }
</script>

<main>
	<h1>Hello {uppercaseName}, I'm {age} years old!</h1>

	<button on:click={incrementAge}>Change Age</button>

	<form id="form">
		<div class="form__row-name">
			<label for="name">Name</label>
			<input name="name" type="text" bind:value={name} />
		</div>
		<div class="form__row-jobTitle">
			<label for="job-title">Job Title</label>
			<input name="job-title" type="text" bind:value={jobTitle} />
		</div>
		<div class="form__row-imgSrc">
			<label for="image-src">Image url</label>
			<input name="image-src" class="input--imgSrc" type="text" bind:value={imageSrc}>
		</div>
		<div>
			<label for="description">Description</label>
			<textarea name="description" id="description" rows="4" bind:value={description} />
		</div>
		<div class="form__row-btn">
			<button on:click|preventDefault={addContact}>Add Contact Card</button>
			<button on:click|preventDefault={deleteFirst}>Delete First</button>
			<button on:click|preventDefault={deleteLast}>Delete Last</button>
		</div>
	</form>

	{#if formState === 'invalid'}
		<p>Invalid input.</p>
	{:else}
		<p>Please enter some  data and hit the button!</p>
	{/if}

	{#each createdContacts as contact, i (contact.id)}
		<h2 class="contact__card--number"># {i + 1}</h2>
		<ContactCard
			name={contact.name}
			description={contact.desc}
			jobTitle={contact.jobTitle}
			imageSrc={contact.imageUrl}
		/>
	{:else}
		<p>Please start adding some contacts, we found none!</p>
	{/each}

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.contact__card--number {
		text-align: left;
	}

	form {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		gap: 10px;
		margin: 2em 0;
	}

	#form {
    width: 30rem;
    max-width: 100%;
  }

	form > div {
		flex-grow: 1;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		column-gap: 5px;
		row-gap: 3px;
	}

	.form__row-btn {
		width: 100%;
		display: flex;
		justify-content: start;
	}

	label {
		display: block;
	}

	input, textarea, button {
		margin: 0;
	}

	input, textarea {
		flex-grow: 1;
		flex-shrink: 1;
		width: 100%;
	}

	.form__row-jobTitle {
		flex-basis: 50%;
	}

	.form__row-imgSrc {
		flex-basis: 100%;
	}

	h1 {
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>