<script lang="ts">
	import { webSearchParameters } from "$lib/stores/webSearchParameters";
	import CarbonInformation from "~icons/carbon/information";
	import Switch from "./Switch.svelte";

	const toggle = () => ($webSearchParameters.useSearch = !$webSearchParameters.useSearch);
</script>

<div
	class="flex h-8 cursor-pointer select-none items-center gap-2 rounded-lg border bg-white p-1.5 shadow-sm hover:shadow-none dark:border-gray-800 dark:bg-gray-900"
	on:click={toggle}
	on:keydown={toggle}
	aria-checked={$webSearchParameters.useSearch}
	aria-label="web search toggle"
	role="switch"
	tabindex="0"
>
	<Switch name="useSearch" bind:checked={$webSearchParameters.useSearch} on:click on:keydown />
	<div class="whitespace-nowrap text-sm text-gray-800 dark:text-gray-200">ウェブ検索</div>
	<div class="group relative w-max">
		<CarbonInformation class="text-xs text-gray-500" />
		<div
			class="pointer-events-none absolute -top-20 left-1/2 w-max -translate-x-1/2 rounded-md bg-gray-100 p-2 opacity-0 transition-opacity group-hover:opacity-100 dark:bg-gray-800"
		>
			<p class="max-w-sm text-sm text-gray-800 dark:text-gray-200">
				有効にすると、モデルはウェブから取得した情報を使って回答を補完しようとします。
			</p>
		</div>
	</div>
</div>
