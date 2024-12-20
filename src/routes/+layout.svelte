<script>
	import '../app.css';
	import Navbar from '$lib/Navbar.svelte';
	export let children;

	let isSidebarOpen = false;

	const toggleSidebar = () => {
		isSidebarOpen = !isSidebarOpen;
	};

	const navItems = [
		{ display: 'About', to: '/about' },
		{ display: 'Blog', to: '/blog' }
	];
</script>

<div class="h-full w-full flex">
	<Navbar {navItems} {toggleSidebar} {isSidebarOpen} />
	<main class="flex-1 bg-gray-50 p-4">{@render children()}</main>
</div>
