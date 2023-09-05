<script lang="ts">
	import 'iconify-icon';
	import type { IMenu } from '../../utils/types/menu';
	let menuItem: IMenu[] = [
		{
			name: 'Keyboards',
			secondMenuItem: [
				{
					name: 'Envoy'
				},
				{
					name: 'Sonet'
				}
			]
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
	let activeSubItem: number | null = null;

	function handleMouseEnter(index: number) {
		activeItem = index;
	}

	function handleMouseEnterSubmenu(index: number) {
		activeSubItem = index;
	}

	function handleMouseLeave() {
		activeItem = null;
	}

	function handleMouseLeaveSubmenu() {
		activeSubItem = null;
	}
</script>

<div class="flex flex-row gap-10 relative">
	{#each menuItem as item, index}
		<div
			class:activeItem
			class="header-item cursor-pointer flex items-center gap-2"
			on:mouseenter={() => handleMouseEnter(index)}
			on:mouseleave={handleMouseLeave}
			aria-hidden="true"
		>
			<span class="header-item--text">{item.name}</span>
			{#if item.secondMenuItem}
				<iconify-icon
					icon="mdi:chevron-down"
					class={`rotate-chevron ${activeItem === index ? 'rotate-180' : ''}`}
					data-icon="bx:bx-home"
				/>
			{/if}

			{#if activeItem === index && item.secondMenuItem}
				<div class="submenu-item absolute">
					{#each item?.secondMenuItem as secondItem, secondIndex}
						<div
							class:activeSubItem
							class="flex submenu-item__container"
							on:mouseenter={() => handleMouseEnterSubmenu(secondIndex)}
							on:mouseleave={handleMouseLeaveSubmenu}
							aria-hidden="true"
						>
							<span class="submenu-item--text flex justify-center items-center"
								>{secondItem.name}</span
							>
							<iconify-icon
								icon="mdi:chevron-down"
								class={`rotate-chevron -rotate-90`}
								data-icon="bx:bx-home"
							/>
						</div>
					{/each}
				</div>
			{/if}
		</div>
	{/each}
</div>

<style lang="scss">
	@import '../../assets/scss//header/headerList.scss';
	@import '../../assets/scss//header/subMenuItem.scss';
</style>
