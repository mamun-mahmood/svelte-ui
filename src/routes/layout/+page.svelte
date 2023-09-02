<div class="grid grid-cols-4 md:grid-cols-12 grid-rows-6 h-screen">
	<div class="hidden md:grid col-span-6 row-span-6">
		<div class="bg-blue-400 col-span-2 row-span-3" />
		<div class="bg-rose-100 col-span-4 row-span-5" />
		<div class="bg-teal-400 col-span-2 row-span-2" />
		<div class="bg-fuchsia-400 row-span-1 col-span-6" />
	</div>
	<div class="grid col-span-4 md:col-span-6 row-span-6">
		<div class="bg-blue-400 hidden md:block row-span-2 col-span-6" />
		<div class="bg-rose-100 col-span-6 row-span-3 md:hidden" />
		<div
			class="bg-yellow-100 col-span-6 md:col-span-4 row-span-3 md:row-span-4 flex items-center justify-center relative"
		>
			<div class="outer-square flex items-center justify-center">
				<div class="inner-circle bg-yellow-100">
					<div class="mountain-container" />
				</div>
			</div>
		</div>

		<div class="bg-emerald-400 hidden md:block col-span-2 row-span-4" />
	</div>
</div>

<style>
	.outer-square {
		background-color: #293462;
		width: 300px;
		height: 300px;
		position: relative;
	}
	.inner-circle {
		width: 200px;
		height: 200px;
		border-radius: 50%;
		overflow: hidden;
	}
	.mountain-container {
		margin-top: auto;
		height: 100%;
		background-color: #fe5f55;
		clip-path: polygon(
			0 100%,
			25% 50%,
			50% 100%,
			75% 50%,
			100% 100%
		); /* Adjust the points to control the mountain shape */
		z-index: -1;
	}
</style>
