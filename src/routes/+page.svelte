<script lang="ts">
	import * as config from '$lib/config';
	import App from '@/components/App.svelte';
</script>

<svelte:head>
	<title>{config.title}</title>
</svelte:head>

<App />
