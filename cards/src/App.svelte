<script>
	import SimpleCard from './lib/SimpleCard.svelte';
	import SocialCard from './lib/SocialCard.svelte';
	import DetailCard from './lib/DetailCard.svelte';
	import avatar from './assets/datboi.jpeg';
</script>

<!--
  style api:
    --card-bg
    --card-padding
    --card-content-size
    --card-title-align
    --card-title-size
    --card-title-bg
    --card-title-hover
-->

<SimpleCard
	style="--card-bg: azure; --card-title-bg: beige; --simple-card-content-size: 16px"
	title="Wow a Simple Card"
	mainContent="This is a Simple Card. Not much to it really, just some text, This is a Simple Card. Not much to it really, just some text."
/>
<SocialCard
	href="https://mikecurry.dev"
	{avatar}
	name="Dat Boi"
	mainContent="Dat Boi is a prolific writer and entrepenuer from San Fransisco."
/>
<DetailCard
  style="--card-title-bg: red;--card-title-hover: orange;--card-bg: azure"
	title="A Simple Detail Card"
	mainContent="Click the button below to see more details"
	detail="Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt hic a et saepe, assumenda, quidem aliquid placeat tempora alias labore modi facilis alias odio vel voluptas eos modi excepturi ut, ipsum, non ex saepe eligendi. Iste suscipit veritatis praesentium ad quia molestiae omnis ratione. Quod soluta eligendi quisquam minima sapiente, ratione fugit. Adipisci aut eum quae, et beatae neque optio consequuntur illum ipsum quod nostrum rem, modi iusto laboriosam amet dolorem odio deleniti molestiae. Magni maiores dolorum voluptates ducimus atque quasi doloribus ab eum, natus, pariatur suscipit et corporis tempore dolore dolores minima temporibus vero soluta. Nemo doloremque officia delectus, sequi cumque nam iste!"
/>

<style>
	:root {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans',
			'Helvetica Neue', sans-serif;
	}
	/* :global(*) {
    margin: 0;
    padding: 0;
  } */
</style>
