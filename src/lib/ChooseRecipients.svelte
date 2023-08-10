<script>
    import RecipientSelectionComponent from "./RecipientSelectionComponent.svelte";

    export let activePage = ""

    let schoolSelected = false
    let apprenticeshipSelected = false

    let openedDropdown = ""

    function handleSubmit() {
        activePage = "pageThree"
    }

    function handleBack() {
        activePage = "pageOne"
    }

    let teachers = ["M. Abplanalp", "A. Baumgartner", "S. Annen", "F. Maurer"]

    let apprenticeshipPeople = ["Lehrmeister", "Praxisbildner", "HR"]

    function openDropdown(e) {
        openDropdown = e.target.InnerText
    }

    function handleSchoolDropdown() {
        openedDropdown = openedDropdown == "" ? "school" : ""
    }

    function handleApprenticeshipDropdown() {
        openedDropdown = openedDropdown == "" ? "apprenticeship" : ""
    }

</script>


<section>
    <h2>
        Empfänger auswählen
    </h2>

    <fieldset>
        <RecipientSelectionComponent 
        title={"Schule"}
        recipients={teachers} />

        <RecipientSelectionComponent
        title={"Lehrbetrieb"}
        recipients={apprenticeshipPeople} />
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
