<script>
	let Question = "Placeholder";
	let Option1 = "Option 1";
	let Option2 = "Option 2";
	let Option3 = "Option 3";
	let Option4 = "Option 4";
</script>

<sveltekit:head>
	<title>BoomBox - Record</title>
	<meta name="description" content="BoomBox - Recorder, but not a recorder" />
</sveltekit:head>
<div class="@container flex flex-col">
	<header class="@container/header text-center text-red-950">
		<h1 class="text-4xl md:text-5xl">BoomBox - Record</h1>
		<h3 class="text-2xl md:text-3xl">This ain't a recorder</h3>
		<h3 class="text-2xl md:text-3xl">Yeahhhh, good luck mate 🇬🇧</h3>
	</header>
	<main class="text-center">
		<h2 class="my-10 text-3xl text-red-950 md:text-4xl">{Question}</h2>
		<div class="@container/options my-auto flex flex-col">
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
			>
				{Option1}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
			>
				{Option2}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
			>
				{Option3}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
			>
				{Option4}
			</button>
		</div>
	</main>
</div>
