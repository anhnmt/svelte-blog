<script lang="ts">
	import { page } from '$app/stores';
	import { routes } from '$lib/config';
	import { cn } from '$lib/utils';
	import { ThemeToggle } from '$lib/components/site';
	import type { PageData } from '../../../routes/blog/$types';

	// export let data: PageData;
</script>

<nav
	class="z-50 top-0 left-0 right-0 h-14 md:h-[4.1rem] border-b fixed supports-[backdrop-filter]:bg-background/60 w-full bg-background/95 backdrop-blur hidden md:block"
>
	<div class="flex items-center justify-between h-full p-4">
		<div>
			<a
				href="/"
				class="text-3xl font-semibold tracking-wider md:text-4xl"
				style="font-family: 'Fuggles', cursive;"
			>
				<span
					class="text-5xl text-transparent bg-gradient-to-r from-primary to-gray-400 bg-clip-text md:text-6xl"
					>P</span
				>rabhu
			</a>
		</div>
		<div class="hidden md:block">
			<div class="flex space-x-4">
				<ul class="flex items-center">
					<!-- <Search {data} /> -->

					{#each routes as route}
						<li>
							<a
								href={route.link}
								class="relative inline-block px-3 py-1 text-lg tracking-wider rounded-lg group hover:bg-accent hover:text-accent-foreground"
							>
								<span
									class={cn(
										'absolute rounded-full -bottom-1 left-1/2 transform -translate-x-1/2 w-4 h-[3px] bg-black dark:bg-white opacity-0 group-hover:opacity-100 transition-opacity',
										$page.url.pathname.startsWith(route.link) ? 'opacity-100' : ''
									)}
								/>
								{route.name}
							</a>
						</li>
					{/each}
				</ul>
				<ThemeToggle />
			</div>
		</div>
	</div>
</nav>
