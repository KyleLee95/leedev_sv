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

<!-- Top bar with menu icon (hidden on large screens) -->
<div class="top-bar">
	<button class="menu-button" on:click={toggleSidebar} aria-label="Open sidebar"> ☰ </button>
	<h1>
		<a href="/"> Kyle Lee </a>
	</h1>
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

<style>
	li {
		list-style: none;
	}

	a {
		text-decoration: none;
		color: inherit;
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

		.close-button {
			display: none; /* Hide the close button on larger screens */
		}
	}
</style>
