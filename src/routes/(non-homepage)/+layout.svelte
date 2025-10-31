<script>
	import { House } from "@lucide/svelte";
	import { goto } from "$app/navigation";

	let { children } = $props();
</script>

<button
	onclick={goto("/")}
	aria-label="Go to Home Page"
	title="Go to Home Page"
	class="relative top-4 left-2 rounded-full bg-white p-2 shadow-lg hover:bg-gray-100 focus:ring-2 focus:ring-blue-500 focus:outline-none"
>
	<House />
</button>
{@render children?.()}
