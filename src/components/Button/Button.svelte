<script lang="ts">
	export let type: string;
	export let buttonHref: string;
	export let buttonText: string;
	export let customStyle: string;

	function selectButtonType() {
		switch (type) {
			case 'transparent':
				return 'custom-button--transparent';

			default:
				return 'custom-button--default';
		}
	}
</script>

<a href={buttonHref} class={`custom-button ${selectButtonType()} ${customStyle}`}>{buttonText} </a>

<style lang="scss">
	.custom-button {
		text-align: center;
		padding: 8px 18px;
		width: 100%;

		&--default {
			color: $color-white;
			background-color: $color-primary;
		}

		&--transparent {
			color: $color-primary;
			background-color: transparent;
			border: 1px solid $color-primary;

			&:hover {
				background-color: $color-primary;
				color: $color-white;
			}
		}
	}
</style>
