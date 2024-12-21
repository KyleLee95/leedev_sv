<script lang="ts">
	import '../app.css';
	import SiteHeader from '$lib/components/site-header.svelte';
	import { ModeWatcher } from 'mode-watcher';
	let { children } = $props();
	import { browser } from '$app/environment';
</script>

{#if browser}
	<ModeWatcher />
{/if}
<div class="w-screen h-screen mx-auto">
	<main class="w-full h-screen">
		<SiteHeader />
		<div class="container">
			{@render children?.()}
			<div></div>
		</div>
	</main>
</div>
