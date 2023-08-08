<script>
    import EmailPreview from "../lib/EmailPreview.svelte";
    import Reason from "../lib/Reason.svelte";

    let selectedReason = ""
    let expectedDelay = ""
    let explanation = ""

    let activePage = "pageOne"
</script>


{#if activePage == "pageOne"}
    <Reason 
    bind:selectedReason={selectedReason}
    bind:expectedDelay={expectedDelay}
    bind:explanation={explanation}
    bind:activePage={activePage} />
{/if}

{#if activePage == "pageTwo"}
    <EmailPreview 
    bind:selectedReason={selectedReason}
    bind:expectedDelay={expectedDelay}
    bind:explanation={explanation}
    bind:activePage={activePage} />
{/if}