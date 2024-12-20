<script>
	let isSidebarOpen = false;

	const toggleSidebar = () => {
		isSidebarOpen = !isSidebarOpen;
	};

	const navItems = [
		{ display: 'About', to: '/about' },
		{ display: 'Blog', to: '/blog' }
	];
</script>

<svelte:head>
	<title>Kyle Lee</title>
</svelte:head>

<div class="container">
	<!-- Top bar with menu icon (hidden on large screens) -->
	<div class="top-bar">
		<button class="menu-button" on:click={toggleSidebar} aria-label="Open sidebar"> ☰ </button>
		<h1>Kyle Lee</h1>
	</div>

	<!-- Sidebar (static or sliding based on screen size) -->
	<div class="sidebar" class:open={isSidebarOpen}>
		<button class="close-button" on:click={toggleSidebar} aria-label="Close sidebar">✕</button>
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

	<!-- Main Content -->
	<main id="content">main content here</main>
</div>

<style>
	/* General styles */
	/* body { */
	/* 	margin: 0; */
	/* 	font-family: Arial, sans-serif; */
	/* } */

	li {
		list-style: none;
	}

	a {
		text-decoration: none;
		color: inherit;
	}

	.container {
		display: flex;
		flex-direction: column;
		height: 100vh;
	}

	/* Top bar styles */
	.top-bar {
		display: flex;
		align-items: center;
		justify-content: space-between;
		background-color: #333;
		color: white;
		padding: 10px 20px;
	}

	.menu-button {
		background: none;
		border: none;
		color: white;
		font-size: 1.5rem;
		cursor: pointer;
	}

	/* Sidebar styles */
	.sidebar {
		position: fixed;
		top: 0;
		left: -250px;
		width: 250px;
		height: 100%;
		background-color: #f4f4f4;
		box-shadow: 2px 0 5px rgba(0, 0, 0, 0.2);
		transition: left 0.3s ease-in-out;
	}

	.sidebar.open {
		left: 0;
	}

	.close-button {
		background: none;
		border: none;
		font-size: 1.5rem;
		cursor: pointer;
		margin-bottom: 20px;
		display: block;
	}

	/* Main content styles */
	#content {
		flex: 1;
		padding: 20px;
		text-align: center;
	}

	/* Responsive styles */
	@media (min-width: 768px) {
		/* Hide top bar on larger screens */
		.top-bar {
			display: none;
		}

		/* Sidebar becomes static */
		.sidebar {
			display: block;
			position: static;
			width: 250px;
			height: auto;
			box-shadow: none;
			left: 0;
		}

		.sidebar.open {
			left: 0; /* This is redundant on large screens but safe */
		}

		.container {
			display: grid;
			grid-template-columns: 250px 1fr; /* Sidebar takes 250px, content takes remaining space */
		}

		#content {
			text-align: left;
		}

		.close-button {
			display: none; /* Hide the close button on larger screens */
		}
	}
</style>
