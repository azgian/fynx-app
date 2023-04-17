<script>
	import logo from '$lib/images/logo_fynx.png';
	// Your selected Skeleton theme:
	import '@skeletonlabs/skeleton/themes/theme-skeleton.css';
	// This contains the bulk of Skeletons required styles:
	import '@skeletonlabs/skeleton/styles/all.css';
	// Finally, your application's global stylesheet (sometimes labeled 'app.css')
	import '../app.postcss';
	import { AppShell } from '@skeletonlabs/skeleton';
	import { AppBar } from '@skeletonlabs/skeleton';
	import AccountCircle from 'svelte-material-icons/AccountCircle.svelte';
	import MenuSide from './MenuSide.svelte';
	import MenuBottom from './MenuBottom.svelte';
</script>

<AppShell
	regionPage="relative"
	slotPageHeader="sticky top-0 z-10"
	slotSidebarLeft="bg-surface-900"
	slotPageFooter="bg-surface-900 z-10"
>
	<svelte:fragment slot="sidebarLeft">
		<div id="sidebar-wrap">
			<div id="sidebar-box">
				<div id="logo-box">
					<a href="/">
						<img src={logo} alt="logo" />
					</a>
				</div>
				<MenuSide />
			</div>
		</div>
	</svelte:fragment>
	<svelte:fragment slot="pageHeader">
		<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
			<svelte:fragment slot="lead">
				<div id="user-box">
					<AccountCircle />
					<span class="mb_name">회원명</span>
				</div>
			</svelte:fragment>
			<svelte:fragment slot="trail" />
		</AppBar>
	</svelte:fragment>
	<slot />
	<svelte:fragment slot="pageFooter">
		<div id="nav-bottom">
			<MenuBottom />
		</div>
	</svelte:fragment>
</AppShell>

<style>
	#nav-bottom {
		display: none;
	}
	#sidebar-wrap {
		position: relative;
		display: flex;
		justify-content: end;
		width: 320px;
	}
	#sidebar-box {
		min-width: 220px;
		/* border: solid #ddd 1px; */
	}
	#logo-box {
		width: 100%;
		padding: 35px 0;
		/* border: solid #eee 1px; */
	}
	#logo-box img {
		width: 180px;
		margin: 0 auto;
		/* border: solid #eee 1px; */
	}
	#user-box {
		display: flex;
		justify-content: start;
		align-items: center;
		font-size: 2rem;
	}
	#user-box .mb_name {
		margin-left: 10px;
		font-size: 1.25rem;
	}
	/* Extra small devices (portrait phones, less than 360px) */
	@media (max-width: 369.98px) {
	}
	/* Extra small devices (portrait phones, less than 576px) */
	@media (max-width: 505.98px) {
	}
	/* Extra small devices (portrait phones, less than 576px) */
	@media (max-width: 575.98px) {
	}
	/* Small devices (landscape phones, less than 768px) */
	@media (max-width: 767.98px) {
	}
	/* Medium devices (tablets, less than 992px) */
	@media (min-width: 768px) and (max-width: 991.98px) {
	}
	@media (max-width: 1020.98px) {
		#sidebar-wrap {
			display: none;
		}
		#nav-bottom {
			display: block;
			position: fixed;
			bottom: 0px;
			left: 0px;
			width: 100vw;
			height: 100px;
			background: rgb(21, 21, 71);
		}
	}
	@media (max-width: 1120.98px) {
		/* nav {left:0px;margin-left:0;padding-bottom:100px;} */
		#sidebar-wrap {
			max-width: 220px;
		}
	}
</style>
