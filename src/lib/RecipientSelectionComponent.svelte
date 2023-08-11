<script>
    import { onMount } from "svelte";

    export let title = ""
    export let recipients = new Map()

    let isExpanded = false

    let allSelected = false

    function handleDropdown() {
        isExpanded = !isExpanded
    }

    function selectRecipient(recipient) {
        recipients.set(recipient, !recipients.get(recipient))

        allSelected = areAllSelected()
    }

    function updateSelectedRecipients() {

    }

    function handleSelectAll() {
        if (allSelected) deselectAll()
        else selectAll()

        allSelected = !allSelected
    }

    function selectAll() {
        for (let key of recipients.keys()) {
            recipients.set(key, true)
        }
    }

    function deselectAll() {
        for (let key of recipients.keys()) {
            recipients.set(key, false)
        }
    }

    function areAllSelected() {
        for (let status of recipients.values()) {
            if (!status) return false
        }
        return true
    }

    onMount(() => {
        console.log("recipient component", recipients)
        for (let recipient of recipients) {
            recipient[1] = false
        }
    })
</script>


<div class="areaWrapper">
    <div  class="inputWrapper {isExpanded ? "expanded" : ""}">
        <label for="{title}">
            <input on:change={handleDropdown} id="{title}" name="{title}" type="checkbox" />
            {title}
        </label>
    </div>

    {#if isExpanded}
        <ul>
            <li>
                <button on:click={handleSelectAll} value="all"
                    class="{allSelected ? "selected" : ""}">

                    {allSelected ? "Alle abwählen" : "Alle auswählen"}

                </button>
            </li>
            {#each recipients as recipient}
                <li>
                    <button class:selected={recipient[1]}
                    on:click={() => selectRecipient(recipient)} value="{recipient}">
                        {recipient[0]}
                    </button>
                </li>
            {/each}
        </ul>
    {/if}
</div>


<style>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
        width: 100%;
        max-height: 200px;
        box-shadow: 0 0 0 1px black;
        overflow-y: scroll;
        overflow-x: hidden;
        gap: 1px;
        display: flex;
        flex-direction: column;
        margin-bottom: 1em;
    }

    .selected {
        background: gray;
        color: white;
    }

    li {
        width: 100%;
    }

    li button {
        padding: 1em;
        font-size: 1rem;
        display: block;
        width: 100%;
        text-align: left;
        border: none;
        cursor: pointer;
    }

    ul, li:last-child button {
        border-bottom-left-radius: .5em;
        border-bottom-right-radius: .5em;
    }

    .expanded {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.363);
        border-bottom-left-radius: 0 !important;
        border-bottom-right-radius: 0 !important;
        box-shadow: 0 0 0 1px black;
    }

    .areaWrapper {
        display: flex;
        width: 100%;
        flex-direction: column;
    }

    .inputWrapper {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1em;
        border-radius: .5em;
        transition: all .1s ease;
    }

    .inputWrapper:hover:not(.expanded) {
        background: rgb(245, 245, 245);
    }

    label {
        display: flex;
        align-items: center;
        gap: 1em;
        width: 100%;
        padding: 1em;
        cursor: pointer;
    }
</style>