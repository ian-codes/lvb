<script>
    export let activePage = ""

    let attemptedSubmit = false

    let reasons = ["Krankheit", "Verspätung", "Anderer"]

    export let selectedReason = ""
    export let expectedDelay = ""
    export let explanation = ""

    function validate() {
        if (selectedReason == "") return false
        if (selectedReason == "Verspätung" && expectedDelay == "") return false
        if (explanation == "") return false

        return true
    }

    function handleSubmit() {
        attemptedSubmit = true
        
        if (!validate()) return

        activePage = "pageTwo"
    }

    function handleReset() {
        selectedReason = ""
        explanation = ""
        expectedDelay = ""
    }
</script>


<form on:submit={handleSubmit}>
    <fieldset>
        <legend class="{(attemptedSubmit && selectedReason == "") ? "warning" : ""}">
            Grund:
        </legend>
    
        {#each reasons as reason}
            <div class="{selectedReason === reason ? "selected" : ""}">
                <input type="radio" id="{reason}" name="reason" value="{reason}"
                on:change={() => selectedReason = reason} />
                <label for="{reason}">{reason}</label>
            </div>
        {/each}
    </fieldset>
    
    <fieldset>
        <label for="erklaerung">Erläuterung:</label>
        <textarea class="{(attemptedSubmit && explanation == "") ? "warning" : ""}"
        bind:value={explanation} id="erklaerung" name="erklaerung" placeholder="Hier kurz genauer erklären"></textarea>
    </fieldset>

    {#if selectedReason === "Verspätung"}
    <fieldset>
        <label for="zeit">Geschätzte Verspätung</label>
        <input class="{(attemptedSubmit && expectedDelay == "") ? "warning" : ""}"
        bind:value={expectedDelay} type="text" name="zeit" id="zeit" placeholder="z.B. 30 Minuten"/>
    </fieldset>
    {/if}

    <div class="buttonsContainer">
        <button type="submit">OK</button>
        <button type="button" on:click={handleReset}>Zurücksetzen</button>
    </div>
</form>

<div>
    <p>
    </p>
</div>



<style>
    form {
        display: flex;
        flex-direction: column;
    }

    fieldset {
        border: none;
        display: flex;
        flex-direction: column;
        background: white;
        gap: .5em;
    }

    fieldset > div {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1em;
        padding-left: .5em;
        border-radius: .5em;
        transition: all .1s ease;
    }

    fieldset > div:hover:not(.selected) {
        background: rgb(245, 245, 245);
    }

    .selected {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.363);
    }

    input, textarea {
        border-radius: none;
        margin: 0;
        font-size: 1em;
        padding: .5em;
        font-family: monospace;
        border: 1px dotted;
        box-shadow: 1px 2px 3px inset rgba(0, 0, 0, 0.123);
    }

    label {
        display: block;
        width: 100%;
        padding: 1em 0;
        cursor: pointer;
    }

    textarea {
        height: 80px;
        width: 100%;
        box-sizing: border-box;
        resize: none;
    }

    .buttonsContainer {
        margin: 1em 0;
        display: flex;
        flex-direction: column;
        gap: 1em;
    }

    button:first-child {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
    }

    .warning {
        box-shadow: 0 0 0 2px red !important;
    }
</style>
