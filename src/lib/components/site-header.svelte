<script lang="ts">
	import { Github, Linkedin } from 'lucide-svelte/icons';
	import { buttonVariants } from '$lib/components/ui/button/index.js';
	import { cn } from '$lib/utils.js';
	import ModeToggle from './mode-toggle.svelte';
	import MainNav from './main-nav.svelte';
	import MobileNav from './mobile-nav.svelte';
</script>

<header
	class="border-border/40 bg-background/95 supports-[backdrop-filter]:bg-background/60 sticky top-0 z-50 w-full border-b backdrop-blur"
>
	<div class="container flex h-14 max-w-screen-2xl items-center">
		<MainNav />
		<MobileNav />
		<div class="flex flex-1 items-center justify-between space-x-2 md:justify-end">
			<div class="w-full flex-1 md:w-auto md:flex-none">
				<!-- <CommandMenu /> -->
			</div>
			<nav class="flex items-center">
				<a target="_blank" href="https://github.com/KyleLee95">
					<div
						class={cn(
							buttonVariants({
								size: 'sm',
								variant: 'ghost'
							}),
							'h-8 w-8 px-0'
						)}
					>
						<Github class="h-4 w-4" />
						<span class="sr-only">GitHub</span>
					</div>
				</a>
				<a target="_blank" href="https://www.linkedin.com/in/kyle-lee-7b39ab1a6/">
					<div
						class={cn(
							buttonVariants({
								size: 'sm',
								variant: 'ghost'
							}),
							'h-8 w-8 px-0'
						)}
					>
						<Linkedin />
						<span class="sr-only">Linkedin</span>
					</div>
				</a>
				<ModeToggle />
			</nav>
		</div>
	</div>
</header>
