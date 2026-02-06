<script lang="ts">
	import TrendRadar from '$lib/components/TrendRadar.svelte';
</script>

<div class="max-w-4xl mx-auto py-12 px-4 sm:px-6">
	<div class="mb-12 text-center">
		<h1 class="text-4xl font-black text-gray-900 mb-4 tracking-tighter">SvelteKit + AI Blog</h1>
		<p class="text-lg text-gray-600">Ajan destekli içerik yönetim sistemi.</p>
	</div>

	<TrendRadar />

	<div class="mt-12 text-center text-sm text-gray-400 font-medium">
		Visit <a href="https://svelte.dev/docs/kit" class="text-orange-600 hover:underline">svelte.dev/docs/kit</a> to read the documentation
	</div>
</div>
