<script>
    import ChooseRecipients from "../lib/ChooseRecipients.svelte";
    import EmailPreview from "../lib/EmailPreview.svelte";
    import Reason from "../lib/Reason.svelte";

    let selectedReason = ""
    let expectedDelay = ""
    let explanation = ""
    let activePage = "pageOne"

    // let allRecipients = new Map([
    //     ["Lehrbetrieb", ["Lehrmeister", "Praxisbildner", "HR"]],
    //     ["Berufsschule", ["M. Abplanalp", "A. Baumgartner", "S. Annen", "F. Maurer"]],
    //     ["Berufsmaturitätsschule", ["M. Lehmann", "M. Ryth", "A. Baumer"]]
    // ])

    let recipients = new Map([
        ["Lehrbetrieb", new Map([
            ["Lehrmeister", false], 
            ["Praxisbildner", false], 
            ["HR", false]])
        ],
        ["Berufsschule", new Map([
            ["M. Abplanalp", false], 
            ["A. Baumgartner", false], 
            ["S. Annen", false], 
            ["F. Maurer", false]]),
        ],
        ["Berufsmaturitätsschule", new Map([
            ["M. Lehmann", false], 
            ["M. Ryth", false], 
            ["A. Baumer", false]])
        ]
    ])

    let selectedRecipients = new Map()
</script>


{#if activePage == "pageOne"}
    <Reason 
    bind:selectedReason={selectedReason}
    bind:expectedDelay={expectedDelay}
    bind:explanation={explanation}
    bind:activePage={activePage} />
{/if}

{#if activePage == "pageTwo"}
    <ChooseRecipients
    bind:activePage={activePage}
    bind:recipients={recipients} />
{/if}

{#if activePage == "pageThree"}
    <EmailPreview 
    bind:selectedReason={selectedReason}
    bind:expectedDelay={expectedDelay}
    bind:explanation={explanation}
    bind:activePage={activePage}
    bind:selectedRecipients={selectedRecipients} />
{/if}