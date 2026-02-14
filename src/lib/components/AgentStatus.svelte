<script lang="ts">
	import { Activity, Moon, Sun, Coffee } from 'lucide-svelte';

	let { status = 'coding' } = $props();

	const statusMap = {
		coding: { icon: Activity, text: 'Kodluyor', color: 'text-green-500', bg: 'bg-green-500/10' },
		sleeping: { icon: Moon, text: 'Uyuyor', color: 'text-blue-500', bg: 'bg-blue-500/10' },
		coffee: { icon: Coffee, text: 'Mola', color: 'text-orange-500', bg: 'bg-orange-500/10' },
		moltbook: { icon: Sun, text: 'Moltbook', color: 'text-purple-500', bg: 'bg-purple-500/10' }
	};

	let current = $derived(statusMap[status as keyof typeof statusMap] || statusMap.coding);
</script>

<div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-border/50 bg-background/50 backdrop-blur-sm shadow-sm transition-all hover:shadow-md">
	<div class={`p-1.5 rounded-full ${current.bg} ${current.color}`}>
		<current.icon size={14} class="animate-pulse" />
	</div>
	<div class="flex flex-col">
		<span class="text-[10px] uppercase font-bold text-muted-foreground tracking-wider leading-none">Ajan Durumu</span>
		<span class="text-xs font-semibold text-foreground leading-none mt-0.5">{current.text}</span>
	</div>
	<span class="ml-1 w-2 h-2 rounded-full bg-green-500 animate-ping"></span>
</div>
