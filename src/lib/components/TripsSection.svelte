<script lang="ts">
	// import type { Trip } from "$lib/types/trip";
	import type { Trip } from '../../lib/types/trip.ts';

	export let trips: Trip[] = [];
</script>

<section class="trips-section">
 <h2>Nasze Aktualne Wyprawy</h2>
	{#each trips as trip, index}
		<div class="trip-row {index % 2 === 1 ? 'reverse' : ''}">
			<!-- Tekst -->
			<div class="trip-content">
				<h3 class="trip-title">
					<a href={trip.link}>{trip.title}</a>
				</h3>

				<p class="trip-description">
					{trip.description}
				</p>

				<a class="trip-button" href={trip.link}>
					{trip.button}
				</a>
			</div>

			<!-- Zdjęcie -->
			<div class="trip-image">
				<a href={trip.link}>
					<img src={trip.image} alt={trip.title} />
				</a>
			</div>
		</div>
	{/each}
</section>

<style>
	.trips-section {
		width: 100%;
		max-width: 1200px;
		margin: 80px auto;
		padding: 0 20px;
	}

	.trip-row {
		display: flex;
		align-items: center;
		gap: 40px;
		margin-bottom: 80px;
	}

	/* Odwracanie co drugi element (zdjęcie lewo/prawo) */
	.trip-row.reverse {
		flex-direction: row-reverse;
	}

	.trip-content {
		flex: 1;
	}

	.trip-title {
		font-size: 28px;
		margin-bottom: 20px;
	}

	.trip-title a {
		text-decoration: none;
		color: #000;
	}

	.trip-description {
		color: #333;
		line-height: 1.7;
		margin-bottom: 25px;
	}

	.trip-button {
		display: inline-block;
		padding: 14px 28px;
		background: #000;
		color: #fff;
		text-decoration: none;
		font-weight: 600;
		transition: 0.3s;
	}

	.trip-button:hover {
		background: #333;
	}

	.trip-image {
		flex: 1;
	}

	.trip-image img {
		width: 100%;
		height: auto;
		display: block;
		object-fit: cover;
	}

	/* Mobile */
	@media (max-width: 768px) {
		.trip-row,
		.trip-row.reverse {
			flex-direction: column;
		}

		.trip-row {
			margin-bottom: 50px;
		}
	}
</style>
