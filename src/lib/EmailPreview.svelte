<script>
    import { onMount } from "svelte";

    export let selectedReason = ""
    export let expectedDelay = ""
    export let explanation = ""
    export let activePage = ""

    let email = ""

    const startingString = "Guten Tag \n \n Auf Grund "

    const endString = `\n \n Erläuterung der Umstände: ${explanation} \n \n` + "Für meine Abwesenheit bitte ich um Entschuldigung. \n \n"
    + "Vielen Dank für Ihr Verständnis. \n \n Freundliche Grüsse"

    function generateEmail() {
        switch(selectedReason) {
            case "Krankheit":
                email = startingString + "von Krankheit werde ich heute leider nicht anwesend sein können." + endString
                break;
            case "Verspätung":
                email = startingString + "einer Verspätung werde ich etwas später kommen müssen. \n \n Geschätzte Verspätung: " + expectedDelay + endString
                break;
            case "Anderer":
                email = startingString + "einer kurzfristiger und unvorhersehbahrer Situation werde ich heute leider nicht annwesend sein können." + endString
                break;
        }
    }

    function handleSubmit() {
        // send emails
    }

    function handleBack() {
        activePage = "pageTwo"
    }

    onMount(() => generateEmail())
</script>


<section>
    <h2>
        Email-Vorschau
    </h2>

    <div>
        <h3>
            Betreff:
        </h3>
        <p>Abwesenheitsmitteilung</p>
    </div>

    <div>
        <h3>
            Inhalt:
        </h3>
        <p>{email}</p>
    </div>

    <div class="buttonsContainer">
        <button class="button" on:click={handleSubmit}>Absenden</button>
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

    h3, p {
        margin: .5em;
    }

    p {
        white-space: pre-line;
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
