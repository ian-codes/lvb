<script>
    import { onMount } from "svelte";
    import RecipientSelectionComponent from "./RecipientSelectionComponent.svelte";

    export let activePage = ""
    export let recipients

    function handleSubmit() {
        updateSelectedRecipients()
        activePage = "pageThree"
    }

    function updateSelectedRecipients() {
        
    }

    function handleBack() {
        activePage = "pageOne"
    }
</script>


<section>
    <h2>
        Empfänger auswählen
    </h2>

    <fieldset>
        {#each [...recipients] as [title, recipients]}
            <RecipientSelectionComponent
            title={title}
            bind:recipients={recipients} />
        {/each}
    </fieldset>

    <div class="buttonsContainer">
        <button class="button" on:click={handleSubmit}>Email generieren</button>
        <button class="button" on:click={handleBack}>Zurück</button>
    </div>
</section>


<style>
    h2 {
        font-size: 1em;
        font-weight: normal;
        opacity: .8;
        letter-spacing: 1px;
        margin: .5em;
        padding: 0;
    }

    fieldset {
        border: none;
        display: flex;
        flex-direction: column;
        align-items: start;
        background: white;
        gap: 8px;
    }

    .buttonsContainer {
        margin: 1em 0;
        display: flex;
        flex-direction: column;
        gap: 1em;
        padding: 0 .5em
    }

    button:first-child {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
        position: relative;
    }
</style>
