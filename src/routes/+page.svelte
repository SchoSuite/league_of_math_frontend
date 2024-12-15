<script lang="ts">
	import { onDestroy, onMount } from 'svelte';
	import { io, Socket } from 'socket.io-client';

	let socket: Socket | null;

	onMount(() => {
		socket = io('http://localhost:3000');

		socket?.on('connect', () => {
			console.log('Connection established');
		});

		socket?.on('disconnect', () => {
			console.log('Connection ended');
		});
	});

	onDestroy(() => {
		socket?.disconnect();
	});
</script>
