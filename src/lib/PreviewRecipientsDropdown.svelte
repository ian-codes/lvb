<script>
    import {base} from "$app/paths"
    import { onMount } from "svelte";

    export let title = ""
    export let recipients = []

    let isExpanded = false

    function handleDropdown() {
        isExpanded = !isExpanded
    }
</script>


<div class="recipientsContainer">
    <div>
        <button on:click={handleDropdown} class="buttonDropdownRecipients">
            {title}
            <div style="background-image: url('{base}/down.png')" 
            class="arrow {isExpanded ? "arrowExpanded" : ""}"></div>
        </button>

        {#if isExpanded}
            <ul>
                {#each recipients as recipient}
                    <li>{recipient}</li>
                {/each}
            </ul>
        {/if}
    </div>
</div>


<style>
    div {
        background: skyblue;
        border-radius: 1em;
        box-shadow: 1px 1px 1px 1px inset rgba(255, 255, 255, 0.521), 1px 1px 1px 1px rgba(0, 0, 0, 0.281), 0 2px 5px rgba(0, 0, 0, 0.164);
    }
    
    .arrow {
        width: 10px;
        height: 10px;
        background-position: center;
        background-size: contain;
        background-repeat: no-repeat;
        transition: all .2s ease;
    }

    .arrowExpanded {
        transform: rotate(-180deg);
    }

    .buttonDropdownRecipients {
        background: none;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: .5em;
        border: none;
        padding: .5em;
        border-radius: 1em;
        box-shadow: 1px 1px 1px 1px inset rgba(255, 255, 255, 0.521), 1px 1px 1px 1px rgba(0, 0, 0, 0.281), 0 2px 5px rgba(0, 0, 0, 0.164);
    }

    ul {
        font-size: .8em;
        list-style: none;
        padding: .5em;
        margin: 0;
        display: flex;
        flex-direction: column;
        gap: .5em;
    }
</style>