<script>
	import BaseCard from './BaseCard.svelte';
	export let title;
	export let mainContent;
	export let width = 320;
	export let style = '';
</script>

<BaseCard {width} {style}>
	<div class="title">{title}</div>
	<p class="content">{mainContent}</p>
	<slot name="action"/>
</BaseCard>

<style>
	.title {
		text-align: var(--card-title-align, center);
		font-size: var(--card-title-size, 18px);
		font-weight: bold;
		padding: var(--card-padding, 16px);
		border-radius: calc(var(--card-padding, 16px) / 2) calc(var(--card-padding, 16px) / 2) 0 0;
		background-color: var(--card-title-bg, #aaa);
	}

	.content {
		font-size: var(--card-content-size, 16px);
		margin: 0;
		height: 100%;
		padding: var(--card-padding, 16px);
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
