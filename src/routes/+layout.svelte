<!-- nts: applies to all routes -->

<script>
	import '../app.css';
	let { children } = $props();
</script>

<main>
	{@render children()}
</main>
