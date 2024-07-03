<script lang="ts">
	import { writable } from 'svelte/store';
	import QRCode from '$lib/QRCode.svelte';

	let inputText = writable('');
</script>

<main>
	<h1>QR Code Generator</h1>
	<input bind:value={$inputText} placeholder="Enter text here" type="text" />
	<QRCode text={$inputText} />
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
	}

	input {
		padding: 0.5rem;
		font-size: 1rem;
	}
</style>
