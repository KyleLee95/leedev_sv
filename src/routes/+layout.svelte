<script>
	import '../app.css';
	import Navbar from '$lib/Navbar.svelte';

	let { children } = $props();
</script>

<div class="container">
	<Navbar />
	<main id="content">
		{@render children()}
	</main>
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		height: 100vh;
	}
	#content {
		flex: 1;
		padding: 20px;
		text-align: center;
	}

	/* Responsive styles */
	@media (min-width: 768px) {
		/* Hide top bar on larger screens */

		.container {
			display: grid;
			grid-template-columns: 250px 1fr; /* Sidebar takes 250px, content takes remaining space */
		}

		#content {
			text-align: left;
		}
	}
</style>
