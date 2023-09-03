<script>
	import HeaderItem from './HeaderList.svelte';
</script>

<div class="header-container flex justify-between">
	<img
		src="https://modedesigns.com/cdn/shop/t/15/assets/mode-logo-5.svg?v=58025636982540038891662147391"
		alt="log"
	/>
	<HeaderItem />

	<button>
		<span>Bag</span>
	</button>
</div>

<style lang="scss">
	.header-container {
		position: fixed;
		padding: 0 30px;
		backdrop-filter: blur(8px);
		background-color: $color-background;
		width: 100%;
	}
</style>
