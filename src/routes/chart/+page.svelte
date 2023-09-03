<script>
	import '../../app.css';
	import { onMount } from 'svelte';
	import { apiData, countries } from '../../store/countryDataStore';
	onMount(async () => {
		fetch('https://restcountries.com/v3.1/all')
			.then((response) => response.json())
			.then((data) => {
				apiData.set(data);
			})
			.catch((error) => {
				console.log(error);
				return [];
			});
	});
</script>

<div class="w-screen p-5">
	<table
		class="table-auto w-full border-separate border-slate-200 border-2 border-spacing-5 rounded-md"
	>
		<thead>
			<tr>
				<th>Flag</th>
				<th>Name</th>
				<th>Population</th>
				<th>CIOC</th>
				<th>UN Member Staus</th>
				<th>Currencies</th>
				<th>Language</th>
			</tr>
		</thead>
		<tbody>
			{#each $countries as { name, cioc, currencyCode, flag, languages, population, unMember }}
				<tr class="text-center border border-t-2 border-b-2 border-slate-200">
					<td>{flag}</td>
					<td>{name}</td>
					<td>{population}</td>
					<td>{cioc}</td>
					{#if unMember}
						<td class="p-2 flex justify-center">
							<p class="w-10 rounded-md" style="background-color: #A2A9B0">Yes</p>
						</td>
					{:else}
						<td class="p-2 flex justify-center"
							><p class="w-10 rounded-md" style="background-color: #656C73">No</p></td
						>
					{/if}
					<td>{currencyCode}</td>
					<td>{languages}</td>
				</tr>
			{/each}
		</tbody>
	</table>
</div>
