<script>
	import { page } from '$app/stores';
	import ChartLine from 'svelte-material-icons/ChartLine.svelte';
	import SyncCircle from 'svelte-material-icons/SyncCircle.svelte';
	import SwapHorizontalBold from 'svelte-material-icons/SwapHorizontalBold.svelte';
	import MessageText from 'svelte-material-icons/MessageText.svelte';
	import AccountCheck from 'svelte-material-icons/AccountCheck.svelte';
	import CogOutline from 'svelte-material-icons/CogOutline.svelte';
	const routesDirArr = [
		{ dirName: 'Chart', icon: ChartLine },
		{ dirName: 'Market', icon: SwapHorizontalBold },
		{ dirName: 'Exch', icon: SyncCircle },
		{ dirName: 'Board', icon: MessageText },
		{ dirName: 'Office', icon: AccountCheck },
		{ dirName: 'Sys', icon: CogOutline }
	];
	// import { testText } from './LogoutTimer.svelte';
	//on:click={timerReset} logoutLimitedTime, logoutTime,
</script>

<nav id="menu-side">
	{#each routesDirArr as routesDir, i}
		<li>
			<a
				class={$page.url.pathname === '/' + routesDir.dirName.toLowerCase() ? 'current' : undefined}
				href="/{i === 0 ? '' : routesDir.dirName.toLowerCase()}"
			>
				<div class="path_name-box">
					<svelte:component this={routesDir.icon} />
					<span class="path_name">{routesDir.dirName}</span>
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
		color: #fca3f4;
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
