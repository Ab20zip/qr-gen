<script lang="ts">
	import { onMount } from 'svelte';
	import QRCode from 'qrcode';

	export let text: string = '';

	let canvas: HTMLCanvasElement;

	onMount(() => {
		if (text) {
			generateQRCode(text);
		}
	});

	async function generateQRCode(text: string) {
		try {
			await QRCode.toCanvas(canvas, text);
		} catch (err) {
			console.error(err);
		}
	}

	$: if (text) {
		generateQRCode(text);
	}
</script>

<canvas bind:this={canvas}></canvas>

<style>
	canvas {
		max-width: 100%;
		height: auto;
	}
</style>
