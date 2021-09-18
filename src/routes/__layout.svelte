<script>
	import '../app.postcss';
</script>

<slot />

<footer class="w-full py-5 sm:py-10 px-4 bg-gray-800">
	<h2 class="sr-only">Footer</h2>
	<div class="flex flex-col-reverse sm:flex-row md:justify-between lg:justify-around">
		<div
			class="relative mt-14 sm:mt-0 px-5 flex flex-col justify-center items-center text-gray-500"
		>
			<h1 class="font-title text-4xl text-center font-semibold mt-auto">NewsletterIO</h1>

			<div class="mt-auto flex flex-col items-center">
				<span class="inline-flex mt-6 w-full justify-center md:justify-start md:w-auto">
					<a href="#link" class="text-gray-200">
						<span class="sr-only">Github</span>
						<svg
							width="24px"
							height="24px"
							fill="currentColor"
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							class="w-8 h-8"
							viewBox="0 0 24 24"
							><path
								d="M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z"
							/></svg
						>
					</a>

					<a href="https://twitter.com/matiasfha" class="ml-3 text-gray-200">
						<span class="sr-only">Twitter</span>
						<svg
							fill="currentColor"
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							class="w-6 h-6"
							viewBox="0 0 24 24"
						>
							<path
								d="M23 3a10.9 10.9 0 01-3.14 1.53 4.48 4.48 0 00-7.86 3v1A10.66 10.66 0 013 4s-4 9 5 13a11.64 11.64 0 01-7 2c9 5 20 0 20-11.5a4.5 4.5 0 00-.08-.83A7.72 7.72 0 0023 3z"
							/>
						</svg>
					</a>
				</span>

				<span class="py-4 text-xs">Made by Matías Hernández.</span>
			</div>

			<span
				class="sm:hidden absolute -top-4 left-1/2 w-1/4 h-px bg-gray-400 transform -translate-x-1/2"
				aria-hidden="true"
			/>
		</div>

		<div class="grid grid-cols-2 gap-5 text-gray-400">
			<div class="col-span-2 md:col-span-1 pb-0 md:py-3 px-4">
				<h3
					class="py-1.5 md:py-4 text-center sm:text-left text-xl text-gray-500 font-bold tracking-wide"
				>
					More?
				</h3>
				<nav class="flex justify-around md:flex-col font-medium list-none">
					<li><a href="https://matiashernandez.dev" class="hover:text-gray-200">Site</a></li>
					<li>
						<a href="https://microbytes.dev/" class="hover:text-gray-200">Newsletter (Spanish)</a>
					</li>
					<li>
						<a href="https://tl.matiashernandez.dev/" class="hover:text-gray-200">Polywork</a>
					</li>
					<li>
						<a href="https://matiasfha.dev/egghead" class="hover:text-gray-200"
							>Courses and Lessons on egghead.io</a
						>
					</li>
					<li><a href="https://cafecon.tech/" class="hover:text-gray-200">Podcast</a></li>
					<li>
						<a href="https://matiasfha.dev/consulting" class="hover:text-gray-200"
							>Consulting and Mentoring</a
						>
					</li>
				</nav>
			</div>

			<div
				class="col-span-2 md:col-span-1 pb-0 md:py-3 px-4 flex flex-col items-center sm:items-start"
			>
				<h3 class="py-1.5 md:py-4 text-xl text-gray-500 font-bold tracking-wide">Fancy Company</h3>
				<p class="inline-flex justify-center sm:justify-start text-sm text-gray-400 font-medium">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="mr-1 h-5 w-5"
						viewBox="0 0 20 20"
						fill="currentColor"
					>
						<path d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z" />
						<path d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z" />
					</svg>
					<a href="mailto:hola@matiashernandez.dev">hola@matiashernandez.dev</a>
				</p>
			</div>
		</div>
	</div>
</footer>
