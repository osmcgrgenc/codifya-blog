<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import AgentStatus from '$lib/components/AgentStatus.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="fixed top-4 right-4 z-50">
	<AgentStatus status="coding" />
</div>

{@render children?.()}
