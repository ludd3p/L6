<script>
    import { createEventDispatcher } from "svelte";
    export let movie;

    const dispatch = createEventDispatcher();

    function handleDelete(e) {
        if (e.key === "Enter" || e.type === "click") {
            dispatch("delete", movie);
        }
    }
</script>

<div class="container">
    <h2>{movie.title}</h2>
    <div class="right">
        <div class="rating">
            {#each Array.from({ length: movie.rating }, (_, i) => i + 1) as _, i}
                <img src="images/star.png" alt="star" class="star" />
            {/each}
        </div>
        <img src="images/delete.png" alt="delete" on:click={handleDelete} on:keydown={handleDelete} class="delete"/>
    </div> 
</div>

<style>
    h2 {
        margin-left: 0.25rem;
    }
    .container {
        display: flex;
        flex-direction: row;
        align-items: center;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 0 1rem;
        margin-bottom: 0.5rem;
        background-color: #e6e6e688;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);

    }
    .right {
        margin-left: auto;
        display: flex;
        flex-direction: row;
    }
    .rating {
        display: flex;
    }

    .star {
        width: 20px;
        height: 20px;
    }
    .delete {
        width: 20px;
        height: 20px;
        cursor: pointer;
    }
</style>