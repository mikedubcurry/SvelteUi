<script>
	import BaseCard from './BaseCard.svelte';
	export let avatar;
	export let name;
	export let href;
	export let mainContent;
	export let width = 320;
	export let style = '';
</script>

<BaseCard {style} {width}>
	<a {href}>
		<div class="title">
			<img src={avatar} alt={`avatar for ${name}`} class="avatar" />
			<span>{name}</span>
		</div>
		<p class="content">{mainContent}</p>
	</a>
</BaseCard>

<style>
	.title {
		display: flex;
		align-items: center;
		font-size: var(--card-title-size, 18px);
		font-weight: bold;
		padding: var(--card-padding, 16px);
		border-radius: calc(var(--card-padding, 16px) / 2) calc(var(--card-padding, 16px) / 2) 0 0;
		background-color: var(--card-title-bg, #aaa);
	}
	a {
		text-decoration: none;
		color: var(--card-text-color, #111);
	}
	.avatar {
		height: var(--avatar-size, 80px);
		border-radius: 50%;
		margin-right: var(--card-padding, 16px);
	}
	.content {
		padding: var(--card-padding, 16px);
	}
</style>
