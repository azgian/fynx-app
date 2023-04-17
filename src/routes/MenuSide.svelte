<script>
	import { page } from '$app/stores';
	const routesDirArr = ['Chart', 'Market', 'Exch', 'Board', 'Office', 'Sys'];
	import ChartLine from 'svelte-material-icons/ChartLine.svelte';
	import SyncCircle from 'svelte-material-icons/SyncCircle.svelte';
	import SwapHorizontalBold from 'svelte-material-icons/SwapHorizontalBold.svelte';
	import MessageText from 'svelte-material-icons/MessageText.svelte';
	import AccountCheck from 'svelte-material-icons/AccountCheck.svelte';
	import CogOutline from 'svelte-material-icons/CogOutline.svelte';
</script>

<nav id="menu-side">
	{#each routesDirArr as routesDir, i}
		<li>
			<a
				class={$page.url.pathname === '/' + routesDir.toLowerCase() ? 'current' : undefined}
				href="/{routesDir === 'Chart' ? '' : routesDir.toLowerCase()}"
			>
				<div class="path_name-box">
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
					{:else if i === 5}
						<CogOutline />
					{/if}
					<span class="path_name">{routesDir}</span>
				</div>
			</a>
		</li>
	{/each}
</nav>

<style>
	#menu-side li {
		position: relative;
		list-style-type: none;
	}
	#menu-side li a {
		display: block;
		height: 50px;
		line-height: 50px;
		padding-right: 15px;
		text-align: right;
		border-radius: 25px 0 0 25px;
		color: #60cdf8;
		text-decoration: none;
	}
	#menu-side li a:hover {
		text-decoration: none;
		background: rgba(73, 73, 245, 0.3);
		color: #fff;
	}
	#menu-side li a.current {
		background: var(--header-color);
		color: #f758e9;
	}
	#menu-side li .path_name-box {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding-left: 15px;
		font-size: 2rem;
	}
	.path_name-box .path_name {
		font-size: 1.5rem;
	}
</style>
