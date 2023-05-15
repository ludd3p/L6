<script>
    import Movie from "./Movie.svelte";
    export let movies = [];
    function sort(e) {
        if (e.target.innerText === "Alfabetisk ordning") {
            movies = [...movies].sort((a, b) => a.title.localeCompare(b.title));
        } else {
            movies = [...movies].sort((a, b) => b.rating - a.rating);
        }
    }
</script>

<div class="container">
    <h1>Filmer</h1>
    {#each movies as movie}
        <Movie {movie} on:delete/>
    {/each}
    <div>
        <button on:click={sort}>Alfabetisk ordning</button>
        <button on:click={sort}>Betygsordning</button>
    </div>
</div>
