<script lang="ts">
	import 'iconify-icon';
	import type { IMenu } from '../../utils/types/menu';
	let menuItem: IMenu[] = [
		{
			name: 'Keyboards'
		},
		{
			name: 'Keycaps'
		},
		{
			name: 'Products'
		},
		{
			name: 'Special Projects'
		},
		{
			name: 'Help'
		},
		{
			name: 'Login'
		}
	];

	let activeItem: number | null = null;

	function handleMouseEnter(index: number) {
		activeItem = index;
	}

	function handleMouseLeave() {
		activeItem = null;
	}
</script>

<div class="flex flex-row gap-10">
	{#each menuItem as item, index}
		<div
			class:activeItem
			class="header-item cursor-pointer flex items-center gap-2"
			on:mouseenter={() => handleMouseEnter(index)}
			on:mouseleave={handleMouseLeave}
			aria-hidden="true"
		>
			<span>{item.name}</span>
			<iconify-icon
				icon="mdi:chevron-down"
				class={`rotate-chevron ${activeItem === index ? 'rotate-180' : ''}`}
				data-icon="bx:bx-home"
			/>
		</div>
	{/each}
</div>

<style lang="scss">
	.header-item {
		padding: 15px;
		span {
			font-size: 12px;

			color: $color-primary;
		}

		&:hover span,
		&:hover > iconify-icon {
			color: $color-secondary;
		}
	}

	.rotate-chevron {
		transition: transform 0.8s ease-in-out;
	}
</style>
