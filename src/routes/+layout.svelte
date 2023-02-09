<script lang="ts">
	import '../app.css';
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	import { goto } from '$app/navigation';
	import TailwindIndicator from './components/TailwindIndicator.svelte';

	let inputValue: string;
	const handleClick = () => {
		goto(`/${inputValue}`);
	};

	onMount(() => {
		inputValue = $page.params.slug;
	});

	// $: if ($page.params.slug) {
	// 	inputValue = $page.params.slug;
	// }
	// $: inputValue = $page.params.slug;
</script>

<div class={$page.params.slug ? '' : 'flex h-screen pb-52 justify-center items-center'}>
	<section class="px-8 xs:px-4 lg:px-32 xl:px-60">
		<header class="rounded-t-xl space-y-4 py-6 dark:highlight-white/10">
			<div class="flex items-center">
				<a href="/"><img src="./favicon.png" alt="logo" class="w-14 xl:w-24" /></a>
				<div>
					<a href="/">
						<h2 class="font-extrabold text-2xl sm:text-3xl lg:text-4xl tracking-tight">
							WordWhisper
						</h2></a
					>
					<p class="font-serif text-xs text-slate-500">
						the word that's on the tip of your tongue but you can't bring it to mind.
					</p>
				</div>
			</div>
			<div
				class="group flex relative rounded-md dark:bg-slate-700 dark:focus-within:bg-transparent"
			>
				<svg
					width="20"
					height="20"
					fill="currentColor"
					class="absolute left-3 top-1/2 -mt-2.5 text-slate-400 pointer-events-none group-focus-within:text-blue-500"
					><path
						fill-rule="evenodd"
						clip-rule="evenodd"
						d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
					/></svg
				><input
					type="text"
					placeholder={$page.params.slug || 'Search a word...'}
					class="input font-medium text-slate-300 w-full pl-10 leading-6 bg-transparent"
					on:input={(e) => (inputValue = e.target.value)}
					value={$page.params.slug ? $page.params.slug : ''}
					on:keydown={(event) => (event.key === 'Enter' && inputValue ? handleClick() : null)}
				/>
				<button class="btn self-center" on:click={inputValue ? handleClick : null}>Search</button>
			</div>
		</header>

		<slot />
	</section>
	<TailwindIndicator />
</div>
