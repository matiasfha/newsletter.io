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

	function reset() {
		markdownValue = '';
		resultHTML = '';
	}
</script>

<svelte:head>
	<title>NewsletterIO | Get the html to your email editor</title>
	<meta charset="utf-8" />
	<meta name="robots" content="index, follow" />
	<meta name="author" content="Matias Hernández" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<meta name="og:type" property="og:type" content="website" />
	<meta
		name="description"
		content="Transform your markdown content into ready to use html snippet for your newsletter"
	/>
</svelte:head>

<div class="m-auto max-w-screen-xl px-4 md:px-0 py-12">
	<div class="grid grid-flow-row md:grid-flow-col">
		<div class="flex flex-col justify-center">
			<div class="md:text-5xl text-2xl uppercase font-black">
				A tool for your upcoming newsletter
			</div>
			<div class="text-xl mt-4">
				Transform your carefully crafted markdown content into ready to use HTML snippet to include
				in your newsletter email editor.
				<br />
				<strong>Include any syntax highlight you need</strong>
			</div>
			<div class="my-5 h-16">
				<div
					class="shadow-md font-medium py-2 px-4 text-yellow-100 hidden
				cursor-pointer bg-yellow-600 hover:bg-yellow-500 rounded text-lg text-center w-48"
				>
					Join us now
				</div>
			</div>
		</div>
		<div class="flex md:justify-end w-full -mt-5">
			<div class="bg-dots">
				<div class="shadow-2xl w-full z-10 rounded-full mt-6 ml-0 md:ml-4">
					<img alt="card img" class="rounded-t" src="/newsletter-marketing.jpg" />
					<div class="text-md p-10 bg-white">
						<ol class="list-decimal mx-auto ml-4 leading-tight">
							<li class="py-2">Write your content with markdown.</li>
							<li class="py-2">Add custom css to style the html elements in the form below.</li>
							<li class="py-2">Click the <strong>Transform</strong> button</li>
							<li class="py-2">Copy the resulting HTML shown in the right tab.</li>
							<li class="py-2">Send and Profit!</li>
						</ol>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>

<main
	class="grid grid-rows-2 md:grid-cols-2 gap-4 max-w-screen-xl mx-auto pt-8 h-auto pb-24 px-4 md:px-0"
>
	<form on:submit|preventDefault={handleSubmit} class="w-full">
		<label for="markdown" class="text-2xl font-bold py-2"
			>Markdown Area
			<textarea
				class="w-full h-96 px-3 py-2 bg-white placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
				required
				rows="10"
				name="markdown"
				id="markdown"
				bind:value={markdownValue}
			/></label
		>

		<label for="customCss" class="text-2xl font-bold py-2"
			>Custom css
			<textarea
				class="w-full h-96 px-3 py-2 bg-white placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
				rows="6"
				name="customCss"
				id="customCss"
				bind:value={customCss}
			/></label
		>
		<div class="flex flex-row justify-between gap-16 pt-8">
			<button
				on:click={reset}
				type="reset"
				class="w-full px-3 py-4 text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none"
				>Reset</button
			>
			<button
				class="w-full px-3 py-4 text-white bg-yellow-500 rounded-md hover:bg-yellow-600 focus:outline-none"
				>Transform</button
			>
		</div>
	</form>

	<aside class="w-full flex flex-col items-start">
		<h1>Results</h1>
		<ul class="list-reset flex border-b">
			<li class="-mb-px mr-1">
				<span
					class="bg-white inline-block py-2 px-4 font-semibold hover:text-purple-500 focus:outline-none cursor-pointer"
					class:activeTab={activeTab === 0}
					on:click={() => (activeTab = 0)}>HTML Code</span
				>
			</li>
			<li class="mr-1">
				<span
					class="bg-white inline-block py-2 px-4 hover:text-blue-darker hover:text-purple-500 focus:outline-none cursor-pointer"
					class:activeTab={activeTab === 1}
					on:click={() => (activeTab = 1)}>Preview</span
				>
			</li>
		</ul>
		<div
			class="relative container w-full p-2 mx-auto text-center bg-white border-2 border-t-0 border-gray-300 border-dashed h-[48.5rem] rounded-xl rounded-t-none"
		>
			<div class="italic text-gray-500 text-md text-left">
				{#if activeTab === 1}
					<div>
						{@html resultHTML}
					</div>
				{/if}
				{#if activeTab === 0}
					<div class="flex flex-col items-start gap-4">
						<button
							class="absolute top-2 right-2 h-8 w-auto p-2 flex items-center justify-center rounded-md bg-yellow-300 shadow-md"
							>Copy to clipboard</button
						>
						<pre
							class="flex-wrap whitespace-pre-wrap overflow-x-auto h-full">
				<code>
					{resultHTML}
				</code>
			</pre>
					</div>
				{/if}
			</div>
		</div>
	</aside>
</main>

<style>
	.active {
	}

	.bg-dots {
		background-image: url(https://assets-global.website-files.com/5b5a66e9f3166b36708705fa/5dea7a12bb83ab1f13040de5_cx-dots.svg);
		background-repeat: no-repeat;
	}
</style>
