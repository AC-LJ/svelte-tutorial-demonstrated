<script lang="ts">
	// components
	import ExerciseHeader from "$atoms/ExerciseHeader.svelte";
	import ButtonCustomizable1 from "$atoms/ButtonCustomizable1.svelte";

	// variables
	const colors = [
		"red",
		"orange",
		"yellow",
		"green",
		"royalblue",
		"slateblue",
		"rebeccapurple",
	];

	let selected = colors[0];
	// $: console.log(selected);
</script>

<template lang="pug">
	ExerciseHeader(
		section="Logic",
		startNumber=16,
		topic="Each blocks"
	)

	.button-grid.grid.grid-cols-7.gap-2.p-4.mt-6.text-20.max-w-md
		+each('colors as color, i')
			button(
				aria-label!="{ color }",
				aria-current!="{ selected === color }",
				style!="{`background-color: ${color}; color: ${['yellow', 'orange'].includes(color) ? 'black' : 'white'}; transform: translate(-4px, -4px);`}",
				on:click!="{ () => selected = color}",
			) { i + 1 }
</template>

<style>
	button {
		aspect-ratio: 1;
		border-radius: 50%;
		background: var(--color, #fff);
		transform: translate(-2px, -2px);
		filter: drop-shadow(3px 3px 3px rgba(0, 0, 0, 0.5));
		transition: all 0.1s;
	}

	button[aria-current="true"] {
		transform: none;
		filter: none;
		box-shadow: inset 3px 3px 4px rgba(0, 0, 0, 0.6);
	}
</style>
