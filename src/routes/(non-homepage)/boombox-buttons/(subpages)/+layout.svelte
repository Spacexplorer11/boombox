<script>
	import { ArrowLeft } from "@lucide/svelte";
	import { goto } from "$app/navigation";

	let { children } = $props();
</script>

<button
	onclick={goto("/boombox-buttons")}
	aria-label="Go to BoomBox Buttons Page"
	title="Go to BoomBox Buttons Page"
	class="relative top-4 left-4 rounded-full bg-white p-2 shadow-lg hover:bg-gray-100 focus:ring-2 focus:ring-blue-500 focus:outline-none"
>
	<ArrowLeft />
</button>
{@render children?.()}
