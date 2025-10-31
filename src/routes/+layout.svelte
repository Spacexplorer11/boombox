<script>
	import "../app.css";

	let { children } = $props();
</script>

<div id="sponsor-buttons" class="mt-2 flex flex-row items-center space-x-[70rem] lg:ml-auto">
	<iframe
		src="https://github.com/sponsors/Spacexplorer11/button"
		title="Sponsor Spacexplorer11"
		height="32"
		width="114"
		style="border: 0; border-radius: 6px;"
	></iframe>
	<a href="https://www.buymeacoffee.com/spacexplorer11" target="_blank" class="pointer"
		><img
			src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png"
			alt="Buy Me A Coffee"
			style="height: 60px !important;width: 217px !important;"
		/></a
	>
</div>
{@render children?.()}
