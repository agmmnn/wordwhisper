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
	let resultvalue: number = 16;

	// $: if ($page.params.slug) {
	// 	inputValue = $page.params.slug;
	// }
	// $: inputValue = $page.params.slug;
</script>

<!-- <div class=" items-center flex">
	<a href="https://github.com/agmmnn/wordwhisper">
		<svg viewBox="0 0 24 24" aria-hidden="true" class="h-6 w-6 mt-2 fill-slate-400"
			><path
				fill-rule="evenodd"
				clip-rule="evenodd"
				d="M12 2C6.477 2 2 6.463 2 11.97c0 4.404 2.865 8.14 6.839 9.458.5.092.682-.216.682-.48 0-.236-.008-.864-.013-1.695-2.782.602-3.369-1.337-3.369-1.337-.454-1.151-1.11-1.458-1.11-1.458-.908-.618.069-.606.069-.606 1.003.07 1.531 1.027 1.531 1.027.892 1.524 2.341 1.084 2.91.828.092-.643.35-1.083.636-1.332-2.22-.251-4.555-1.107-4.555-4.927 0-1.088.39-1.979 1.029-2.675-.103-.252-.446-1.266.098-2.638 0 0 .84-.268 2.75 1.022A9.607 9.607 0 0 1 12 6.82c.85.004 1.705.114 2.504.336 1.909-1.29 2.747-1.022 2.747-1.022.546 1.372.202 2.386.1 2.638.64.696 1.028 1.587 1.028 2.675 0 3.83-2.339 4.673-4.566 4.92.359.307.678.915.678 1.846 0 1.332-.012 2.407-.012 2.734 0 .267.18.577.688.48 3.97-1.32 6.833-5.054 6.833-9.458C22 6.463 17.522 2 12 2Z"
			/></svg
		></a
	>
</div> -->

<div class={$page.params.slug ? 'pb-10' : 'flex h-screen justify-center items-center '}>
	<section class="px-8 xs:px-4 lg:px-32 xl:px-60">
		<header class="rounded-t-xl space-y-4 py-6 dark:highlight-white/10">
			<div class="flex items-center">
				<a href="/"><img src="./favicon.png" alt="logo" class="w-14 xl:w-24" /></a>
				<div>
					<a href="/">
						<h1
							class="font-extrabold text-transparent text-2xl bg-clip-text w-fit bg-gradient-to-r from-yellow-300 to-slate-500"
						>
							WordWhisper
						</h1>
					</a>
					<p class="font-serif text-xs text-slate-500">
						the word that's on the tip of your tongue but you can't bring it to mind.
					</p>
				</div>
			</div>
			<div class="group flex relative rounded-md ">
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
				>

				<input
					type="text"
					placeholder={$page.params.slug || 'Search a word...'}
					class="input font-medium text-slate-300 w-full pl-10 leading-6 bg-transparent"
					on:input={(e) => (inputValue = e.target.value)}
					value={$page.params.slug ? $page.params.slug : ''}
					on:keydown={(event) => (event.key === 'Enter' && inputValue ? handleClick() : null)}
				/>

				<!-- Search Button -->
				<button class="btn self-center" on:click={inputValue ? handleClick : null}
					><svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="1.5"
						stroke="currentColor"
						class="w-6 h-6"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
						/>
					</svg>
				</button>

				<!-- Search Settings -->
				<div class="dropdown dropdown-bottom dropdown-end">
					<label tabindex="0" class="btn m-1"
						><svg
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							class="w-6 h-6"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M9.594 3.94c.09-.542.56-.94 1.11-.94h2.593c.55 0 1.02.398 1.11.94l.213 1.281c.063.374.313.686.645.87.074.04.147.083.22.127.324.196.72.257 1.075.124l1.217-.456a1.125 1.125 0 011.37.49l1.296 2.247a1.125 1.125 0 01-.26 1.431l-1.003.827c-.293.24-.438.613-.431.992a6.759 6.759 0 010 .255c-.007.378.138.75.43.99l1.005.828c.424.35.534.954.26 1.43l-1.298 2.247a1.125 1.125 0 01-1.369.491l-1.217-.456c-.355-.133-.75-.072-1.076.124a6.57 6.57 0 01-.22.128c-.331.183-.581.495-.644.869l-.213 1.28c-.09.543-.56.941-1.11.941h-2.594c-.55 0-1.02-.398-1.11-.94l-.213-1.281c-.062-.374-.312-.686-.644-.87a6.52 6.52 0 01-.22-.127c-.325-.196-.72-.257-1.076-.124l-1.217.456a1.125 1.125 0 01-1.369-.49l-1.297-2.247a1.125 1.125 0 01.26-1.431l1.004-.827c.292-.24.437-.613.43-.992a6.932 6.932 0 010-.255c.007-.378-.138-.75-.43-.99l-1.004-.828a1.125 1.125 0 01-.26-1.43l1.297-2.247a1.125 1.125 0 011.37-.491l1.216.456c.356.133.751.072 1.076-.124.072-.044.146-.087.22-.128.332-.183.582-.495.644-.869l.214-1.281z"
							/>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"
							/>
						</svg>
					</label>
					<div
						tabindex="0"
						class="dropdown-content card card-compact w-64 p-2 shadow bg-primary text-primary-content"
					>
						<div class="card-body">
							<h3 class="card-title">Settings</h3>

							Result shown: {resultvalue}
							<input
								type="range"
								min="0"
								max="100"
								bind:value={resultvalue}
								class="range  range-xs"
							/>

							<input
								type="text"
								placeholder="Topic: (eg: color,weather)"
								class="input input-bordered input-sm"
							/>

							<input type="text" placeholder="Start with:" class="input input-bordered input-sm" />

							<input type="text" placeholder="End with:" class="input input-bordered input-sm" />
							<button class="btn self-center" on:click={inputValue ? handleClick : null}
								><svg
									xmlns="http://www.w3.org/2000/svg"
									fill="none"
									viewBox="0 0 24 24"
									stroke-width="1.5"
									stroke="currentColor"
									class="w-6 h-6"
								>
									<path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
								</svg>
								Apply
							</button>
						</div>
					</div>
				</div>
			</div>
		</header>

		<slot />
	</section>
	<TailwindIndicator />
</div>
