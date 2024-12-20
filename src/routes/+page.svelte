<script>
	const navItems = [
		{ display: 'About', to: '/about' },
		{ display: 'Blog', to: '/blog' }
	];
</script>

<svelte:head>
	<title>Kyle Lee</title>
</svelte:head>

<div class="container">
	<div class="grid-item" id="sidebar">
		<ul>
			<li>
				<h1>Kyle Lee</h1>
			</li>
			{#each navItems as navItem}
				<li>
					<a href={navItem.to}>{navItem.display}</a>
				</li>
			{/each}
		</ul>
	</div>

	<main class="grid-item" id="content">main content here</main>
</div>

<style>
	/* Remove bullet points from the list */
	li {
		list-style: none;
	}

	/* Style the sidebar */
	#sidebar {
		display: flex;
		flex-direction: column;
		background-color: #f4f4f4;
		padding: 20px;
	}

	/* Style the main content */
	#content {
		background-color: #ffffff;
		padding: 20px;
		text-align: left;
	}

	/* Create the two-column layout */
	.container {
		display: grid;
		grid-template-columns: 250px 1fr; /* Sidebar takes fixed width, content takes remaining space */
		height: 100vh; /* Full viewport height */
	}

	.grid-item {
		border: 1px solid #ddd;
	}

	/* Center the main content vertically */
	#content {
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 20px;
	}
</style>
