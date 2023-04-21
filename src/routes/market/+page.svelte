<script>
	import { page } from '$app/stores';
	import { fade, blur, fly, slide, scale, draw, crossfade } from 'svelte/transition';
</script>

<div class="container-box">
	<h3 transition:scale>
		{$page.url.pathname}
	</h3>
</div>
