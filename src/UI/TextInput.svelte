<script>
	export let controlType = "input"
	export let type = "text"
	export let value
	export let id
	export let label
	export let rows = '3'

	let autoComplete =
		type === 'email'
			? 'email'
			: type === 'address'
			? 'street-address'
			: type === 'url'
			? 'url'
			: 'on'
</script>

<div class="form-control">
	<label for={id}>{label}</label>
		{#if controlType === 'textarea'}
			<textarea
				rows={rows}
				autocapitalize="sentences"
				autocomplete="on"
				spellcheck="true"
				id={id}
				value={value}
				on:input />
		{:else}
			<input
				autocomplete={autoComplete}
				spellcheck="true"
				type={type}
				id={id}
				value={value}
				on:input />
		{/if}
</div>

<style>
	textarea {
		border-color: var(--primary);
		outline: none;
		resize: none;
	}

	label {
		display: block;
		margin-bottom: 0.5rem;
		width:  100%;
	}

	.form-control {
		padding: 0.5rem 0;
		width: 100%;
		margin: 0.25rem 0;
	}
</style>