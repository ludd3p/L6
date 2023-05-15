<script>
	import MovieList from "./components/MovieList.svelte";
	import MovieForm from "./components/MovieForm.svelte";
	let movies = [];
	const handleSubmit = (e) => {
		movies = [...movies, e.detail];
	};
	function handleDelete(e) {
		const deleteMovie = e.detail;
		movies = movies.filter((movie) => movie !== deleteMovie);
	}
</script>

<div class="app">
	<MovieForm on:submit={handleSubmit} />
	<MovieList {movies} on:delete={handleDelete} />
</div>

<style>
	.app {
		width: 80%;
		max-width: 800px;
		margin: 0 auto;
	}
	@media (max-width: 480px) {
		.app {
			width: 100%;
		}
	}
</style>
