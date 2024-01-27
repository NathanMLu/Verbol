<script lang="ts">
	import "../app.css";
	import Icon from '@iconify/svelte';
	import { onMount } from 'svelte';

	let onBoarded: boolean = false;


	// onMount(() => {
	// 	// onBoarded = checkIfOnboarded();
	// 	console.log(onBoarded)
	// 	if (!onBoarded) {
	// 	window.localStorage.setItem("onboarded", "true");
	// 	}

	// });



	// const checkIfOnboarded = () => {
	// 	const onboarded = window.localStorage.getItem("onboarded");
	// 	console.log(onboarded)
	// 	if (onboarded === "true") {
	// 	return true;
	// 	} else {
	// 	return false;
	// 	}
	// };



  
</script>

<div class="app flex flex-col min-h-screen h-auto">
	<nav class="p-5 h-min">
		<a href="/">
			<img src="./favicon.png" alt="Favicon" class="w-14 h-14" />
		</a>
	</nav>
	<main class="px-5">
		<slot />
	</main>

	<footer class="mt-auto">
		<div class="flex justify-between align-middle h-20">
			<a href="/aac" class="flex justify-center items-center footer-icon ml-8">
				<Icon icon="fluent:chat-32-filled" class="w-12 h-12" />
			</a>
			<a href="/" class="flex justify-center items-center footer-icon">
				<Icon icon="fluent:mic-32-filled" class="w-12 h-12" />
			</a>
			<a href="/settings" class="flex justify-center items-center footer-icon mr-8">
				<Icon icon="fluent:settings-32-filled" class="w-12 h-12" />
			</a>
		</div>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		background: linear-gradient(45deg, #277CC6, #EAEFEE 60%);
	}

	footer {
		background-color: #1F3A4C;
	}

	.footer-icon {
		color: #EAEFEE;
	}

	
</style>