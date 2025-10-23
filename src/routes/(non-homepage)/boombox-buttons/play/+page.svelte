<script>
	import { onMount } from "svelte";

	let megatonnes = $state(0);
	let explosion = "";
	let launch = "";
	let megatonnesInput = "";
	let launcherText = $state("are gonna throw");
	let launchEligible = $derived.by(() => {
		if (megatonnes > 0) {
			return "";
		} else {
			return "disabled";
		}
	});
	let buttonText = $derived.by(() => {
		if (megatonnes > 0) {
			return "Launch";
		} else {
			return "Ineligible for Launch";
		}
	});
	onMount(() => {
		explosion = document.getElementById("explosion");
		launch = document.getElementById("launch");
		megatonnesInput = document.getElementById("megatonnes");
	});
</script>

<sveltekit:head>
	<title>BoomBox - Play</title>
	<meta name="description" content="BoomBox - LAUNCH" />
</sveltekit:head>
<div class="@container flex flex-col">
	<header class="@container/header text-center text-red-950">
		<h1 class="text-4xl md:text-5xl">BoomBox - Play</h1>
		<h3 class="text-2xl md:text-3xl">Launch TNT</h3>
		<h3 class="text-2xl md:text-3xl">Don't be afraid!</h3>
	</header>
	<main class="@container/main mt-10 flex flex-col text-center">
		<label for="megatonnes" class="text-2xl text-red-950 md:text-3xl"
			>How many megatonnes of TNT would you like to throw at a birb?</label
		>
		<input
			id="megatonnes"
			class="mx-auto w-20 invalid:outline-red-500 disabled:cursor-not-allowed"
			bind:value={megatonnes}
			type="number"
		/>
		{#if megatonnes !== null && megatonnes > 1 && megatonnes !== ""}
			<p class="mx-auto max-w-fit text-2xl text-green-700 text-shadow-2xs md:text-3xl">
				You {launcherText}
				{megatonnes} megatonnes of TNT at an innocent birb!
			</p>
		{:else if megatonnes !== null && megatonnes > 0 && megatonnes !== ""}
			<p class="mx-auto text-2xl text-amber-600 text-shadow-2xs md:text-3xl">
				You {launcherText} 1 megatonne of TNT at an innocent birb!
			</p>
		{:else}
			<p class="mx-auto text-2xl text-red-700 text-shadow-2xs md:text-3xl">
				You aren't gonna throw any megatonnes of TNT at an innocent birb :( <br />
				<em>(Enter a positive number > 0)</em>
			</p>
		{/if}
		<button
			id="launch"
			aria-label="confirm"
			class="mx-auto max-w-fit rounded-2xl bg-green-700 p-4 text-red-500 not-disabled:hover:translate-y-1 not-disabled:hover:scale-[1.03] not-disabled:hover:shadow-2xl active:bg-green-800 disabled:cursor-not-allowed disabled:bg-gray-600"
			disabled={launchEligible}
			onclick={() => {
				explosion.style.visibility = "visible";
				launch.style.visibility = "hidden";
				megatonnesInput.disabled = "disabled";
				launcherText = "threw";
			}}
		>
			{buttonText}
		</button>
		<iframe
			id="explosion"
			style="visibility: hidden;"
			class="mx-auto"
			width="560"
			height="315"
			src="https://www.youtube.com/embed/tQ3qPEbbqmg?autoplay=1&mute=1&controls=0"
			title="YouTube video player"
			frameborder="0"
			allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
			referrerpolicy="strict-origin-when-cross-origin"
			allowfullscreen
		></iframe>
	</main>
</div>
