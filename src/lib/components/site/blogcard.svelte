<script lang="ts">
	import type { Post, SeriesPost } from '$lib/types';
	import { cn, formatDate } from '$lib/utils';
	import { ArrowRight, Calendar } from 'lucide-svelte';
	import { Button } from '../ui/button';
	import { Badge } from '../ui/badge';

	export let post: Post | SeriesPost;
	let hover: boolean = false;
</script>

<a
	class={cn('block pb-0 border-2 rounded-xl hover:border-primary no-highlight max-w-md')}
	on:mouseenter={() => (hover = true)}
	on:mouseleave={() => (hover = false)}
	href={`blog/${post.slug}`}
	data-sveltekit-preload-data
>
	{#if post.image}
		<div class="p-2">
			<img src={post.image} alt={post.title} class="rounded-md w-fit" loading="lazy" />
		</div>
	{/if}
	<div class="flex flex-col justify-between h-full gap-4 p-2.5 pt-0">
		<div class="flex flex-col justify-between gap-2">
			<h1 class={`text-lg font-semibold ${hover ? 'underline underline-offset-4' : ''}`}>
				{post.title}
			</h1>
			<div class="flex gap-2">
				{#each post.tags as tag}
					<Badge class="rounded">{tag}</Badge>
				{/each}
			</div>
		</div>
		<div>
			<p class="text-muted-foreground">{post.description}</p>
		</div>

		<div>
			<div class="flex items-center justify-between">
				<div class="flex items-center text-sm gap-2">
					<Calendar class="w-4 h-4" />
					<h1>{formatDate(post.date)}</h1>
				</div>
				<div>
					<Button variant="ghost" size="sm" class="px-3 py-0" href={`/blog/${post.slug}`}
						>read more
						<ArrowRight class={`h-4 w-4 ml-2`} /></Button
					>
				</div>
			</div>
		</div>
	</div>
</a>
