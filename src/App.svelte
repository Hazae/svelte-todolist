<script>
	export let name;
</script>

<main>
<!--	<h1>Hello {name}!</h1>-->
<!--	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>-->
	<section class="hero is-primary is-fullheight">
		<div class="hero-body">
			<div class="container">
				<h1 class="title">Hello {name}!</h1>
				<h2 class="subtitle">
					Visit the
					<a href="https://svelte.dev/tutorial">Svelte tutorial</a>
					to learn how to build Svelte apps.
				</h2>
			</div>
		</div>
	</section>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>