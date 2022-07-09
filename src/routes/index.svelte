<script lang="ts">
	const groups = [
		{
			name: 'Choose your protein',
			items: [
				{
					name: 'Hot Dog',
					description: ''
				},
				{
					name: 'Polish Bratwurst',
					description: ''
				},
				{
					name: 'Chicken Bratwurst',
					description: ''
				}
			]
		},
		{
			name: 'Choose your bun',
			items: [
				{
					name: 'Brioche',
					description: ''
				},
				{
					name: 'Grandma Sycamore',
					description: ''
				},
				{
					name: 'Chicken Bratwurst',
					description: ''
				}
			]
		},
		{
			name: 'Choose your toppings',
			items: [
				{
					name: 'Croque Monsieur',
					description: 'Prosciutto and provolone, torched to perfection'
				},
				{
					name: 'Buffalo Chicken',
					description: 'Buffalo sauce and bleu cheese'
				},
				{
					name: 'Bloody Mary',
					description: 'Bloody mary mix, bacon, celery, peppers, topped with celery salt'
				},
				{
					name: 'Chili',
					description: 'Vegan or meat chili'
				},
				{
					name: 'Slaw',
					description: 'Homemade slaw'
				}
			]
		}
	];

	let selections: string[] = groups.map(() => '');

	const getItemByGroupIndexAndItemIndex = (groupIndex: number, itemIndex: number): string => {
		return groups[groupIndex].items[itemIndex].name;
	};

	const makeSelection = (group: number, item: number) => {
		selections[group] = getItemByGroupIndexAndItemIndex(group, item);
	};
</script>

<div class="max-w-7xl mx-auto py-12 px-8 grid gap-y-8 md:gap-y-16 text-gray-600">
	<h1 class="text-3xl font-bold underline">Bonners' Backyard BBQ</h1>

	{#each groups as group, groupIndex}
		<div class="border-4 border-red-700 rounded-xl py-8 px-8 md:px-16">
			<div class="flex justify-center">
				<h2
					class="text-center uppercase -mt-12 bg-white px-4 lg:px-8 text-red-700 font-bold text-2xl"
				>
					Step {groupIndex + 1}: {group.name}
				</h2>
			</div>
			<div class="grid md:grid-cols-3 gap-3 mt-8 md:mt-2">
				{#each group.items as item, itemIndex}
					<button
						on:click={() => makeSelection(groupIndex, itemIndex)}
						class={`border py-4 px-8 rounded-md hover:bg-red-200 hover:border-red-400 hover:text-red-800 transition-colors ${
							selections[groupIndex] === item.name
								? 'bg-red-100 border-red-300 text-red-700'
								: 'bg-white'
						}`}
					>
						<h3 class="text-xl font-bold">{item.name}</h3>
						<p class="text-sm">{item.description}</p>
					</button>
				{/each}
			</div>
		</div>
	{/each}

	<div class="border py-8 px-4 inline-block">
		<h2>Selections</h2>
		<ul>
			{#each selections as selection, selectionIndex}
				<li>Step: {selectionIndex + 1}: {selection || ''}</li>
			{/each}
		</ul>
	</div>
</div>
