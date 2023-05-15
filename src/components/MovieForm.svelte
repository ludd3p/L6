<script>
    import { createEventDispatcher } from "svelte";
    import Popup from "./Popup.svelte";
    const dispatch = createEventDispatcher();
    let title = "";
    let rating = 0;
    let id = 0;
    let show = false;
    let text = "Du måste fylla i alla fält";

    const handleSubmit = () => {
        if (title.length === 0 || rating === 0) {
            show = true;
            return;
        }

        const newMovie = {
            id: id++,
            title: title,
            rating: rating,
        };
        dispatch("submit", newMovie);
        title = "";
        rating = 0;
    };

    const handlePopupClose = () => {
        show = false;
    };

</script>

<div class="container">
    <h1>Min filmlista</h1>
    <form on:submit|preventDefault={handleSubmit}>
        <fieldset>
            <legend>Lägg till en film</legend>
            <label for="title-field">Titel</label>
            <input
                type="text"
                id="title-field"
                autocomplete="off"
                placeholder="Skriv titel här"
                bind:value={title}
            />
            <label for="rating-field">Rating</label>
            <select
                type="text"
                id="rating-field"
                autocomplete="off"
                bind:value={rating}
            >
                <option value="0" disabled selected>Välj betyg här</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
                <option value="5">5</option>
            </select>
            <button type="submit">Spara film</button>
        </fieldset>
    </form>
    <hr />
</div>
<Popup {show} {text} on:close={handlePopupClose}/>
<style>
    .container {
        width: 100%;
        margin: 0;
        padding: 0;
    }
    h1 {
        margin: 0;
        margin-bottom: 0.5rem;
        padding: 0;
    }
    fieldset {
        border: none;
        margin: 0;
        padding: 0;
    }
    fieldset > legend {
        margin: 0;
        margin-bottom: 0.5rem;
        padding: 0;
        font-size: 1.5rem;
    }
    fieldset > input,
    fieldset > select {
        width: 100%;
        margin-top: 2px;
        border-radius: 5px;
        padding: 0.5rem;
    }
    button {
        background-color: #28a745;
        color: #fff;
        padding: 0.5rem 1rem;
        border: none;
        border-radius: 4px;
        cursor: pointer;
    }
    button:hover {
        background-color: #218838;
    }
    button:focus {
        outline: none;
        box-shadow: 0 0 0 3px rgba(40, 167, 69, 0.5);
    }
    button:disabled {
        background-color: #ccc;
        cursor: not-allowed;
    }
</style>
