<script>
	import Button from '../UI/Button.svelte'
	export let title
	export let subtitle
	export let imageUrl
	export let description
	export let address
	export let id
	export let contactEmail
</script>

<article>
	<header>
		<h1>{title}</h1>
		<h2>{subtitle}</h2>
		<p>{address}</p>
	</header>

	<div class="image">
		<img src={imageUrl} alt={title}>
	</div>

	<div class="content">
		<p>{description}</p>
	</div>

	<footer>
		<Button href="mailto:{contactEmail}" caption="Contact" />
		<Button type="button" caption="Show Details" />
		<Button type="button" caption="Favorite" />
	</footer>
</article>

<style>
	article {
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
		border-radius: 5px;
		background: white;
		/* margin: 1rem; */
	}

	header {
		border: none;
		box-sizing: border-box;
	}

	.content {
		border: none;
		box-sizing: border-box;
		height: 4rem;
	}

	header,
	.content,
	footer {
		padding: 1rem;
	}

	.image {
		width: 100%;
		height: 14rem;
	}

	.image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: center;
	}

	h1 {
		font-size: 1.25rem;
		margin: 0.5rem 0;
		font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
	}

	h1.is-favorite {
    background: #01a129;
    color: white;
    padding: 0 0.5rem;
    border-radius: 5px;
  }

  h2 {
    font-size: 1rem;
    color: #808080;
    margin: 0.5rem 0;
  }

  p {
    font-size: 1.25rem;
    margin: 0;
  }

  div {
    text-align: right;
  }
</style>