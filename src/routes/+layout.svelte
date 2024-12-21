<script lang="ts">
	import '../app.css';
	import * as Sidebar from '$lib/components/ui/sidebar/index.js';
	import AppSidebar from '$lib/components/app-sidebar.svelte';
	import { ModeWatcher } from 'mode-watcher';
	let { children } = $props();
</script>

<ModeWatcher />
<Sidebar.Provider>
	<AppSidebar />
	<div class="w-screen h-screen mx-auto">
		<main class="w-full h-screen">
			<Sidebar.Trigger />
			{@render children?.()}
		</main>
	</div>
</Sidebar.Provider>
