<script>
	import { page } from '$app/stores';
	// const routesDirArr = ['Chart', 'Market', 'Exch', 'Board', 'Office', 'Sys'];
	const routesDirArr = ['Chart', 'Market', 'Exch', 'Board', 'Office'];
	import ChartLine from 'svelte-material-icons/ChartLine.svelte';
	import SyncCircle from 'svelte-material-icons/SyncCircle.svelte';
	import SwapHorizontalBold from 'svelte-material-icons/SwapHorizontalBold.svelte';
	import MessageText from 'svelte-material-icons/MessageText.svelte';
	import AccountCheck from 'svelte-material-icons/AccountCheck.svelte';
	import CogOutline from 'svelte-material-icons/CogOutline.svelte';
	import { fade, blur, fly, slide, scale, draw, crossfade } from 'svelte/transition';
</script>

<nav id="menu-bottom">
	{#each routesDirArr as routesDir, i}
		<li>
			<a
				class={$page.url.pathname === '/' + routesDir.toLowerCase() ? 'current' : undefined}
				href="/{routesDir === 'Chart' ? '' : routesDir.toLowerCase()}"
			>
				<div class="path_name-box" transition:fly>
					{#if i === 0}
						<ChartLine />
					{:else if i === 1}
						<SwapHorizontalBold />
					{:else if i === 2}
						<SyncCircle />
					{:else if i === 3}
						<MessageText />
					{:else if i === 4}
						<AccountCheck />
						<!-- {:else if i === 5}
						<CogOutline /> -->
					{/if}
					<span class="path_name">{routesDir}</span>
				</div>
			</a>
		</li>
	{/each}
</nav>

<style>
	#menu-bottom {
		display: flex;
		justify-content: space-between;
		width: 100%;
		height: 100%;
	}
	#menu-bottom li {
		flex-grow: calc(100 / 5);
		position: relative;
		list-style-type: none;
		height: 100%;
	}
	#menu-bottom li a {
		display: block;
		height: 100%;
		line-height: 100%;
		text-align: center;
		color: #60cdf8;
		text-decoration: none;
	}
	#menu-bottom li a:hover {
		text-decoration: none;
		background: rgba(73, 73, 245, 0.3);
		color: #fff;
	}
	#menu-bottom li a.current {
		background: var(--header-color);
		color: #f758e9;
	}
	#menu-bottom li .path_name-box {
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		font-size: 2.5rem;
	}
	.path_name-box .path_name {
		font-size: 0.85rem;
	}
</style>
