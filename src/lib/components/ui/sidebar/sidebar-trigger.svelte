<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import { cn } from '$lib/utils.js';
	import type { ComponentProps } from 'svelte';
	import { useSidebar } from './context.svelte.js';
	import { Github, Linkedin, Sun, Moon, Menu } from 'lucide-svelte/icons';
	import { resetMode, setMode } from 'mode-watcher';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu/index.js';
	import { buttonVariants } from '$lib/components/ui/button/index.js';

	let {
		ref = $bindable(null),
		class: className,
		onclick,
		...restProps
	}: ComponentProps<typeof Button> & {
		onclick?: (e: MouseEvent) => void;
	} = $props();

	const sidebar = useSidebar();
</script>

<div class="flex flex-row justify-between md:justify-end">
	<Button
		type="button"
		onclick={(e) => {
			onclick?.(e);
			sidebar.toggle();
		}}
		data-sidebar="trigger"
		variant="ghost"
		size="icon"
		class={cn('md:hidden block pl-2 h-7 w-7', className)}
		{...restProps}
	>
		<Menu />
		<span class="sr-only">Toggle Sidebar</span>
	</Button>
	<div class="flex items-center">
		<a target="_blank" href="https://github.com/KyleLee95">
			<Button
				type="button"
				data-sidebar="trigger"
				variant="ghost"
				size="icon"
				class={cn('h-7 w-7', className)}
				{...restProps}
			>
				<Github />
				<span class="sr-only">Toggle Sidebar</span>
			</Button>
		</a>
		<a target="_blank" href="https://www.linkedin.com/in/kyle-lee-7b39ab1a6/">
			<Button
				type="button"
				data-sidebar="trigger"
				variant="ghost"
				size="icon"
				class={cn('h-7 w-7', className)}
				{...restProps}
			>
				<Linkedin />
				<span class="sr-only">Toggle Sidebar</span>
			</Button>
		</a>
		<!-- Theme switcher -->
		<DropdownMenu.Root>
			<DropdownMenu.Trigger class={buttonVariants({ variant: 'ghost', size: 'icon' })}>
				<Sun
					class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
				/>
				<Moon
					class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
				/>
				<span class="sr-only">Toggle theme</span>
			</DropdownMenu.Trigger>
			<DropdownMenu.Content align="end">
				<DropdownMenu.Item onclick={() => setMode('light')}>Light</DropdownMenu.Item>
				<DropdownMenu.Item onclick={() => setMode('dark')}>Dark</DropdownMenu.Item>
				<DropdownMenu.Item onclick={() => resetMode()}>System</DropdownMenu.Item>
			</DropdownMenu.Content>
		</DropdownMenu.Root>
	</div>
</div>
