<script lang="ts">
	import { Github, Linkedin, Sun, Moon, LinkedinIcon } from 'lucide-svelte/icons';
	import { resetMode, setMode } from 'mode-watcher';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu/index.js';
	import { Button } from '$lib/components/ui/button/index.js';
	import { buttonVariants } from '$lib/components/ui/button/index.js';
	import * as Sidebar from './ui/sidebar/index.js';
	import { cn } from '$lib/utils.js';
</script>

<header
	class="border-border/40 bg-background/95 supports-[backdrop-filter]:bg-background/60 sticky top-0 z-50 w-full border-b backdrop-blur"
>
	<div class="container flex h-14 max-w-screen-2xl items-center">
		<!-- <MainNav /> -->
		<!-- <MobileNav /> -->

		<Sidebar.Trigger />
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
						<LinkedinIcon />
						<span class="sr-only">X (formerly known as Twitter)</span>
					</div>
				</a>
			</nav>
		</div>
	</div>
</header>
