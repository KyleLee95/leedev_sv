<script lang="ts">
	import '../app.css';
	import * as Sidebar from '$lib/components/ui/sidebar/index.js';
	import AppSidebar from '$lib/components/app-sidebar.svelte';
	import SiteHeader from '$lib/components/site-header.svelte';
	import { ModeWatcher } from 'mode-watcher';
	let { children } = $props();
</script>

<ModeWatcher />
<Sidebar.Provider>
	<AppSidebar />
	<div class="w-screen h-screen mx-auto">
		<main class="w-full h-screen">
			<SiteHeader />
			<div class="container">
				{@render children?.()}
				<div></div>
			</div>
		</main>
	</div>
</Sidebar.Provider>
