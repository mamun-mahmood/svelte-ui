<script>
	import { topPopulatedCountries } from '../../store/countryDataStore.js';
	import { get } from 'svelte/store';
	import { PolarArea } from 'svelte-chartjs';
	import {
		Chart as ChartJS,
		Title,
		Tooltip,
		Legend,
		ArcElement,
		RadialLinearScale
	} from 'chart.js';
	import { onMount } from 'svelte';
	// setTimeout(() => {
	// }, 2000);
	ChartJS.register(Title, Tooltip, Legend, ArcElement, RadialLinearScale);
	onMount(() => {
		ChartJS.overrides.polarArea.plugins.legend.position = 'bottom';
	});
	// console.log(get(topPopulatedCountries));
	const countries = get(topPopulatedCountries);

	let datasets = [
		{
			data: [],
			backgroundColor: ['#656C73', '#A2A9B0'],
			label: 'My dataset'
		}
	];
	let labels = [];
	countries.map((e) => {
		datasets[0].data.push(e.population);
		labels.push(e.name);
	});
	console.log(datasets);
	const data = { datasets, labels };
</script>

<div class="bg-white">
	<h1 class="border-b-2 p-5 mb-5">Countires</h1>
	<PolarArea {data} options={{ responsive: true }} />
</div>
