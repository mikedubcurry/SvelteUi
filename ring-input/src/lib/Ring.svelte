<script>
	export let size = 200
	export let thickness = 10;

	let scalingFactor = (size - thickness * 2) / size;
	let x = size * scalingFactor;
	let y = size * scalingFactor;
	let stroke;
	let value = 10;
	let focused = false
	$: stroke = `hsl(${value}deg, 50%, 50%)`;
</script>

<div class:focused style={`width: ${size}px; height: ${size}px`}>
	<svg width={size} height={size} viewBox={`0 0 ${size} ${size}`} aria-hidden="true">
		<ellipse
			fill="none"
			stroke="#ddd"
			stroke-width={thickness}
			cx={size / 2}
			cy={size / 2 + thickness / 2}
			rx={x / 2}
			ry={y / 2}
		/>
		<path
			stroke={value === 0 ? '#ddd' : stroke}
			stroke-width={thickness}
			stroke-dashoffset={-value + 100}
			pathLength="100"
			class="ring"
			d={`M ${size / 2 - thickness / 2}, ${size - thickness / 2} A ${x / 2} ${y / 2} 30 1 1 ${
				size / 2 + thickness / 2
			}, ${size - thickness / 2}`}
		/>
	</svg>
	<input
		style={`width: ${size}px; height: ${size}px; left: calc(50% - ${size / 2}px);`}
		type="range"
		bind:value
		max="100"
		min="0"
		step="1"
		on:focus={() => focused = true}
		on:input={() => focused = true}
		on:blur={() => focused = false}
	/>
	{value}
</div>

<style>
	div {
		position: relative;
	}
	.ring {
		stroke-dasharray: 101;
		fill: none;
		stroke-linecap: round;
		transition: all 0.3s ease, stroke 0.5s ease;
	}
	input {
		position: relative;
		top: -100%;
		z-index: 5;
		cursor: grab;
		opacity: 0;
		}
.focused::before {
	width: 100%;
	height: 100%;
	position:absolute;
	content: '';
	border: 2px black solid;
	border-radius: 4px;
	/* left: 0; */
	padding: 5px;
	/* top: 10px; */
}
	input:active {
		cursor: grabbing;
	}
	input::-webkit-slider-thumb {
    -webkit-appearance: none;
  }
  input::-ms-track {
    width: 100%;
    cursor: pointer;

    background: transparent; 
    border-color: transparent;
    color: transparent;
  }

</style>
