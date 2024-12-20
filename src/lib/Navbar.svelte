<script>
	export let navItems = [];
	export let toggleSidebar; // Function to toggle the sidebar
	export let isSidebarOpen; // Boolean to indicate sidebar state
</script>

<div class="flex md:hidden justify-between items-center bg-gray-800 text-white px-4 py-2">
	<!-- Hamburger Menu -->
	<button class="lg:hidden text-2xl" on:click={toggleSidebar} aria-label="Toggle Sidebar">
		☰
	</button>

	<!-- Brand Name -->
	<h1 class="text-xl font-bold">
		<a href="/">Kyle Lee</a>
	</h1>

	<!-- Navbar Links (hidden on small screens) -->
	<ul class="hidden lg:flex space-x-4">
		{#each navItems as { display, to }}
			<li>
				<a href={to} class="hover:text-gray-400">{display}</a>
			</li>
		{/each}
	</ul>
</div>

<div
	class={`fixed top-0 left-0 bg-gray-100 w-64 h-full transform transition-transform duration-300 ${
		isSidebarOpen ? 'translate-x-0' : '-translate-x-full'
	} lg:translate-x-0 lg:static lg:w-64`}
>
	<button class="lg:hidden text-xl absolute top-2 right-2" on:click={toggleSidebar}> ✕ </button>
	<ul class="mt-4 space-y-2 p-4">
		{#each navItems as { display, to }}
			<li>
				<a href={to} class="block text-gray-700 hover:text-gray-900">
					{display}
				</a>
			</li>
		{/each}
	</ul>
</div>
