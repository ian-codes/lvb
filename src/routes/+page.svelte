<script>
    let reasons = ["Krankheit", "Verspätung", "Anderer"]

    let reason = ""
</script>


<h1>Abwesenheitsmelder</h1>

<form>
    <fieldset>
        <legend>Grund:</legend>
    
        {#each reasons as reason}
            <div>
                <input type="radio" id="{reason}" name="reason" value="{reason}" />
                <label for="{reason}">{reason}</label>
            </div>
        {/each}
    </fieldset>
    
    <fieldset>
        <label for="erklaerung">Erläuterung:</label>
        <textarea id="erklaerung" name="erklaerung" placeholder="Hier kurz genauer erklären"></textarea>
    </fieldset>

    <fieldset>
        <label for="zeit">Geschätzte Verspätung</label>
        <input type="text" name="zeit" id="zeit" placeholder="z.B. 30 Minuten"/>
    </fieldset>
</form>

<div>

</div>



<style>
    h1 {
        font-size: 1.5em;
        text-align: center;
        margin-bottom: 2rem;
    }

    form {
        display: flex;
        flex-direction: column;
        gap: 2em;
    }

    fieldset {
        border: none;
        box-shadow: 0 3px 5px rgba(0, 0, 0, 0.082);
        display: flex;
        flex-direction: column;
        background: white;
    }

    div {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1em;
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
    }

    textarea {
        height: 80px;
        min-height: 80px;
        max-height: 80px;
        width: 100%;
        max-width: 100%;
        box-sizing: border-box;
    }
    

</style>
