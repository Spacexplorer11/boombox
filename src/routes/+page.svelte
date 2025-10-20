<script>
	import { goto } from "$app/navigation";
</script>

<sveltekit:head>
	<title>BoomBox - Home</title>
	<meta
		name="description"
		content="BoomBox - In the most literal sense ever. This is based on the Kurzgesagt fandom!"
	/>
</sveltekit:head>
<div class="@container flex flex-col">
	<header class="@container/header text-center text-red-950">
		<h1 class="text-4xl md:text-5xl">BoomBox</h1>
		<h3 class="text-2xl md:text-3xl">In the most literal sense ever</h3>
		<h3 class="text-2xl md:text-3xl">This is based on the Kurzgesagt fandom!</h3>
	</header>
	<main class="@container/main">
		<div class="@container/boombox min-w-full">
			<button
				class="w-full"
				aria-label="Go to BoomBox Buttons Page"
				title="Go to BoomBox Buttons Page"
				onclick={goto("/boombox-buttons")}
			>
				<img
					src="/images/boombox.webp"
					alt="BoomBox"
					class="mx-auto my-4 aspect-[16/9] w-full object-cover"
				/>
			</button>
		</div>
	</main>
</div>
