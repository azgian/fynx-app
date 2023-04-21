<script>
	import { page } from '$app/stores';
	import { fade, blur, fly, slide, scale, draw, crossfade } from 'svelte/transition';
	// 	import { parseXml } from './xml2json.js';

	// 	const xml = `
	//     <catalog>
	//       <book id="bk101">
	//         <author>Gambardella, Matthew</author>
	//         <title>XML Developer's Guide</title>
	//         <genre>Computer</genre>
	//         <price>44.95</price>
	//         <publish_date>2000-10-01</publish_date>
	//         <description>An in-depth look at creating applications
	//           with XML.</description>
	//       </book>
	//       <book id="bk102">
	//         <author>Ralls, Kim</author>
	//         <title>Midnight Rain</title>
	//         <genre>Fantasy</genre>
	//         <price>5.95</price>
	//         <publish_date>2000-12-16</publish_date>
	//         <description>A former architect battles corporate zombies,
	//           an evil sorceress, and her own childhood to become queen
	//           of the world.</description>
	//       </book>
	//     </catalog>
	//   `;
	// 	const xml_json = parseXml(xml);
	// 	const xml_json2 = JSON.parse(xml_json);
	// 	console.log(xml_json2);
</script>

<div class="container-box">
	<div transition:scale>
		<h1>Hello Skeleton</h1>
		<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
		<section>
			<a class="btn variant-filled-primary" href="https://kit.svelte.dev/">SvelteKit</a>
			<a class="btn variant-filled-secondary" href="https://tailwindcss.com/">Tailwind</a>
			<a class="btn variant-filled-tertiary" href="https://github.com/">GitHub</a>
		</section>
	</div>

	<div class="mt-5" transition:scale>
		<div class="coin_list-box block card card-hover p-5" href="/elements/cards">Hover Me!</div>
		<div class="coin_list-box block card card-hover p-5" href="/elements/cards">Hover Me!</div>
		<div class="coin_list-box block card card-hover p-5" href="/elements/cards">Hover Me!</div>
		<div class="coin_list-box block card card-hover p-5" href="/elements/cards">Hover Me!</div>
		<div class="coin_list-box block card card-hover p-5" href="/elements/cards">Hover Me!</div>
	</div>
</div>

<!-- {xml_json2} -->

<style>
	.coin_list-box {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		margin-bottom: 10px;
	}
</style>
