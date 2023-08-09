<script>
    export let activePage = ""

    let schoolSelected = false
    let apprenticeshipSelected = false

    let openedDropdown = ""

    function handleSubmit() {
        activePage = "pageThree"
        console.log(schoolSelected, apprenticeshipSelected)
    }

    function handleBack() {
        activePage = "pageOne"
    }

    let teachers = ["Alle auswählen", "M. Abplanalp", "A. Baumgartner", "S. Annen", "F. Maurer"]

    let apprenticeshipPeople = ["Alle auswählen", "Lehrmeister", "Praxisbildner", "HR"]

    function openDropdown(e) {
        openDropdown = e.target.InnerText
    }
</script>


<section>
    <h2>
        Empfänger auswählen
    </h2>

    <fieldset>
        <div class="areaWrapper">
            <div class="inputWrapper {schoolSelected ? "selected" : ""}">
                <label for="school">
                    <input on:change={() => schoolSelected = !schoolSelected} 
                    id="school" name="school" type="checkbox" />
                    Schule
                </label>
            </div>
    
            {#if schoolSelected}
                <select multiple>
                    {#each teachers as teacher}
                        <option value="{teacher}">{teacher}</option>
                    {/each}
                </select>
            {/if}
        </div>


        <div class="areaWrapper">
            <div class="inputWrapper {apprenticeshipSelected ? "selected" : ""}">
                <label for="apprenticeship">
                    <input on:change={() => apprenticeshipSelected = !apprenticeshipSelected} 
                    id="apprenticeship" name="apprenticeship" type="checkbox" />
                    Lehrbetrieb
                </label>
            </div>
    
            {#if apprenticeshipSelected}
                <select id="apprenticeshipPeople" name="apprenticeshipPeople" multiple>
                    {#each apprenticeshipPeople as person}
                        <option value="{person}">{person}</option>
                    {/each}
                </select>
            {/if}
        </div>
    </fieldset>


    <div class="buttonsContainer">
        <button on:click={handleSubmit}>Email generieren</button>
        <button on:click={handleBack}>Zurück</button>
    </div>
</section>



<style>
    .selected {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.363);
    }

    option {
        padding: 1em;
    }

    h2 {
        font-size: 1em;
        font-weight: normal;
        opacity: .8;
        letter-spacing: 1px;
        margin: .5em;
        padding: 0;
    }

    .areaWrapper {
        display: flex;
        width: 100%;
        flex-direction: column;
    }

    fieldset {
        border: none;
        display: flex;
        flex-direction: column;
        align-items: start;
        background: white;
        gap: 8px;
    }

    .inputWrapper {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1em;
        padding-left: .5em;
        border-radius: .5em;
        transition: all .1s ease;
    }

    .inputWrapper:hover:not(.selected) {
        background: rgb(245, 245, 245);
    }

    label {
        display: flex;
        align-items: center;
        gap: 1em;
        width: 100%;
        padding: 1em 0;
        cursor: pointer;
    }

    .selected {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.363);
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
    }
</style>
