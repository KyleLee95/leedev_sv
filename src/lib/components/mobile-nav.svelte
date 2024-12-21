<script lang="ts">
	import * as Sheet from './ui/sheet/index.js';
	import { Menu } from 'lucide-svelte/icons';
	import { Button } from './ui/button/index.js';
	import MobileLink from './mobile-link.svelte';
	import { ScrollArea } from './ui/scroll-area/index.js';
	import Mobius from './ui/icons/Mobius.svelte';
	import { browser } from '$app/environment';
	const navItems = [
		{
			title: 'About',
			href: '/about'
		},
		{
			title: 'Blog',
			href: '/blog'
		}
	];
	let open = false;
</script>

{#if browser}
	<Sheet.Root bind:open>
		<Sheet.Trigger
			class="mr-2 px-0 text-base hover:bg-transparent focus-visible:bg-transparent focus-visible:ring-0 focus-visible:ring-offset-0 md:hidden"
		>
			<Button variant="ghost">
				<Menu />
				<span class="sr-only">Toggle Menu</span>
			</Button>
		</Sheet.Trigger>

		<Sheet.Content side="left" class="pr-0">
			<MobileLink href="/" class="flex items-center" bind:open>
				<Mobius class="mr-2 h-6 w-6" />
				<span class="font-bold">kylelee.dev</span>
			</MobileLink>
			<ScrollArea orientation="both" class="my-4 h-[calc(100vh-8rem)] pb-10 pl-6">
				<div class="flex flex-col space-y-3">
					{#each navItems as { title, href }}
						<MobileLink {href} {title} bind:open>
							{title}
						</MobileLink>
					{/each}
				</div>
			</ScrollArea>
		</Sheet.Content>
	</Sheet.Root>
{/if}
