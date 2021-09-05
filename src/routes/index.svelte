<script lang="ts">
	let markdownValue = '';
	let customCss = '';
	let resultHTML = '';
	let activeTab = 0;

	async function handleSubmit(event) {
		const res = await fetch('https://matiasfha.dev/.netlify/functions/preMailer', {
			method: 'POST',
			body: JSON.stringify({
				markdown: markdownValue,
				css: customCss
			})
		});
		resultHTML = await res.text();
	}
</script>

<main class="grid grid-cols-2 gap-4 max-w-screen-xl mx-auto">
	<form on:submit|preventDefault={handleSubmit} class="w-full">
		<label for="markdown" class="text-lg font-bold py-2"
			>Markdown Area
			<textarea
				class="w-full px-3 py-2 text-gray-700 border rounded-lg focus:outline-none"
				rows="10"
				name="markdown"
				id="markdown"
				bind:value={markdownValue}
			/></label
		>

		<label for="customCss" class="text-lg font-bold py-2"
			>Custom css
			<textarea
				class="w-full px-3 py-2 text-gray-700 border rounded-lg focus:outline-none"
				rows="6"
				name="customCss"
				id="customCss"
				bind:value={customCss}
			/></label
		>
		<div class="flex flex-row justify-between">
			<button
				class="h-8 w-auto p-2 flex items-center justify-center rounded-md bg-indigo-300 shadow-md"
				>Submit</button
			>
			<button
				on:click={() => {
					markdownValue = '';
					resultHTML = '';
				}}
				type="reset"
				class="h-8 w-auto p-2 flex items-center justify-center rounded-md bg-red-300 shadow-md"
				>Reset</button
			>
		</div>
	</form>

	<aside class="w-full flex flex-col items-start">
		<h1>Results</h1>
		<ul
			class="flex justify-start items-start my-4 border-separate border-b-2 border-indigo-300 w-full"
		>
			<li
				class="cursor-pointer py-2 px-4"
				class:active={activeTab === 0}
				on:click={() => (activeTab = 0)}
			>
				Code
			</li>
			<li
				class="cursor-pointer py-2 px-4 "
				class:active={activeTab === 1}
				on:click={() => (activeTab = 1)}
			>
				Preview
			</li>
		</ul>
		{#if activeTab === 1}
			<div>
				{@html resultHTML}
			</div>
		{/if}
		{#if activeTab === 0}
			<div class="flex flex-col items-start gap-4">
				<button
					class="h-8 w-auto p-2 flex items-center justify-center rounded-md bg-indigo-300 shadow-md"
					>Copy to clipboard</button
				>
				<pre
					class="max-w-4xl shadow-md flex-wrap whitespace-pre-wrap overflow-x-auto h-96">
				<code>
					{resultHTML}
				</code>
			</pre>
			</div>
		{/if}
	</aside>
</main>

<style>
	.active {
		border: 2px gray solid;
		border-bottom: 0;
		border-radius: 5px;
	}
</style>
