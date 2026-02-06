<script lang="ts">
	import { Sparkles, TrendingUp, BookOpen, PenTool } from 'lucide-svelte';

	let { status = 'idle' } = $props();
	
	let trends = $state([
		{ topic: 'Svelte 5 Runes', density: 'High', sentiment: 'Positive' },
		{ topic: 'Edge Computing', density: 'Medium', sentiment: 'Neutral' },
		{ topic: 'AI Agent Workflows', density: 'Ultra', sentiment: 'Excited' }
	]);

	let isAnalyzing = $state(false);

	function startAnalysis() {
		isAnalyzing = true;
		setTimeout(() => {
			isAnalyzing = false;
		}, 2000);
	}
</script>

<div class="rounded-xl border border-orange-200 bg-orange-50 p-6 shadow-sm">
	<div class="flex items-center justify-between mb-6">
		<div class="flex items-center gap-3">
			<div class="p-2 bg-orange-500 rounded-lg text-white">
				<TrendingUp size={20} />
			</div>
			<div>
				<h3 class="text-lg font-bold text-orange-900 leading-none mb-1">İçerik Trend Radarı</h3>
				<p class="text-xs text-orange-700 font-medium uppercase tracking-wider">AI Destekli Analiz</p>
			</div>
		</div>
		<button 
			onclick={startAnalysis}
			disabled={isAnalyzing}
			class="px-4 py-2 bg-orange-600 hover:bg-orange-700 disabled:opacity-50 text-white rounded-lg text-sm font-bold transition-all flex items-center gap-2"
		>
			{#if isAnalyzing}
				<div class="w-4 h-4 border-2 border-white/30 border-t-white rounded-full animate-spin"></div>
				Taranıyor...
			{:else}
				<Sparkles size={16} />
				Gündemi Tara
			{/if}
		</button>
	</div>

	<div class="grid gap-4">
		{#each trends as trend}
			<div class="flex items-center justify-between p-4 bg-white rounded-lg border border-orange-100 group hover:border-orange-300 transition-colors">
				<div class="flex items-center gap-4">
					<div class="w-10 h-10 flex items-center justify-center bg-orange-100 rounded-full text-orange-600">
						<BookOpen size={18} />
					</div>
					<div>
						<p class="font-bold text-gray-900 group-hover:text-orange-700 transition-colors">{trend.topic}</p>
						<div class="flex items-center gap-2 mt-1">
							<span class="text-[10px] font-bold px-2 py-0.5 bg-orange-100 text-orange-700 rounded-full uppercase italic tracking-tighter">
								{trend.density} Yoğunluk
							</span>
							<span class="text-[10px] font-bold text-gray-400">|</span>
							<span class="text-[10px] text-gray-500 font-medium uppercase">{trend.sentiment}</span>
						</div>
					</div>
				</div>
				<button class="p-2 text-gray-400 hover:text-orange-600 hover:bg-orange-50 rounded-lg transition-all" title="Yazı Taslağı Oluştur">
					<PenTool size={18} />
				</button>
			</div>
		{/each}
	</div>

	<div class="mt-6 pt-6 border-t border-orange-200">
		<div class="flex items-center gap-2 text-orange-800 font-bold mb-3">
			<Sparkles size={16} />
			<span class="text-sm italic uppercase tracking-tight text-orange-900 underline decoration-orange-400 decoration-2 underline-offset-4">Bugünkü "Wow" Fikri:</span>
		</div>
		<p class="text-sm text-gray-700 leading-relaxed font-medium bg-white/50 p-4 rounded-lg italic border-l-4 border-orange-400 shadow-inner">
			"Svelte 5 Runes ile State Yönetimi: Ajan Gözüyle Bir Bakış" - Bu başlık şu an Moltbook'ta çok ilgi çeker Çağrı. Teknik detayları ben hazırlarım, sen sadece dokunuşunu yaparsın. 😉
		</p>
	</div>
</div>
