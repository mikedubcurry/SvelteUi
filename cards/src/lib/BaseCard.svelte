<script>
	export let style = '';
  export let width;
</script>

<div class="card" style={`width: ${width}px; ${style}`}>
	<slot />
</div>

<style>
  :global(.card:hover .title) {
    background-color: var(--card-title-hover, #bbb);
  }
  :global(.card .title) {
    transition: background-color .3s ease;
  }
	.card {
    color: var(--card-text-color, #111);
		box-sizing: border-box;
		background-color: var(--card-bg, #ddd);
		border-radius: calc(var(--card-padding, 16px) / 2);
		border: 1px solid #eee;
		box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.4), -1px 1px 5px rgba(0, 0, 0, 0.4), 0 5px 14px rgba(0, 0, 0, 0.2);
		transition: box-shadow 0.5s ease;
    margin: var(--card-margin, 16px);
	}
	.card:hover {
		box-shadow: 1px 2px 8px rgba(0, 0, 0, 0.3), -1px 2px 8px rgba(0, 0, 0, 0.3), 0 7px 20px rgba(0, 0, 0, 0.2);
	}
</style>
