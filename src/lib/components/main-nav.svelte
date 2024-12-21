<script lang="ts">
	import Mobius from '../components/ui/icons/Mobius.svelte';
	import { page } from '$app/state';
	import { cn } from '$lib/utils.js';
</script>

<div class="mr-4 hidden md:flex">
	<a href="/" class="mr-6 flex items-center space-x-2">
		<Mobius class="h-6 w-6" />
	</a>
	<nav class="flex items-center gap-6 text-sm">
		<a
			href="/blog"
			class={cn(
				'hover:text-foreground/80 transition-colors',
				page.url.pathname === '/blog' ? 'text-foreground' : 'text-foreground/60'
			)}
		>
			Blog
		</a>
		<a
			href="/about"
			class={cn(
				'hover:text-foreground/80 transition-colors',
				page.url.pathname.startsWith('/about') ? 'text-foreground' : 'text-foreground/60'
			)}
		>
			About
		</a>
	</nav>
</div>
