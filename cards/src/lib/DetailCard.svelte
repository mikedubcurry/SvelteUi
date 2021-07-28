<script>
	import { fade, fly } from 'svelte/transition';
	import BaseCard from './BaseCard.svelte';
	import SimpleCard from './SimpleCard.svelte';
	import { portal } from './actions/portal.js';
	export let title;
	export let mainContent;
	export let width = 320;
	export let style = '';
	export let detail;
	let isDetailOpen = false;
</script>

<BaseCard {width} {style}>
	<div class="title">{title}</div>
	<p class="content">{mainContent}</p>
	<div class="actions">
		<button on:click={() => (isDetailOpen = true)}>More</button>
	</div>
</BaseCard>
{#if isDetailOpen}
	<div transition:fly={{ y: 100, opacity: 0 }} class="detail" use:portal hidden>
		<slot>
			<SimpleCard {title} mainContent={detail} {width} {style}>
				<div class="detailAction" slot="action"><button on:click={() => (isDetailOpen = false)}>Close</button></div>
			</SimpleCard>
		</slot>
	</div>
	<div transition:fade on:click={() => (isDetailOpen = false)} class="bg-overlay" />
{/if}

<style>
	.title {
		text-align: var(--card-title-align, center);
		font-size: var(--card-title-size, 18px);
		font-weight: bold;
		padding: var(--card-padding, 16px);
		border-radius: calc(var(--card-padding, 16px) / 2) calc(var(--card-padding, 16px) / 2) 0 0;
		background-color: var(--card-title-bg, #aaa);
	}
	.bg-overlay {
		position: fixed;
		padding: 0;
		margin: 0;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.4);
		z-index: 100;
		cursor: pointer;
	}
	.detail {
		position: fixed;
		inset: 0;
		margin: 0 auto;
		z-index: 101;
		max-width: fit-content;
		max-height: fit-content;
	}
	button {
		border: 1px solid #eee;
		border-radius: calc(var(--card-padding, 16px) / 2);
		padding: calc(var(--card-padding, 16px) / 2) var(--card-padding, 16px);
		transition: background-color 0.3s ease;
		background-color: var(--card-title-bg, #aaa);
	}
	button:hover {
		background-color: var(--card-title-hover, #bbb);
	}
	.actions, .detailAction {
		display: flex;
		justify-content: flex-end;
		padding: var(--card-padding, 16px);
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
