<script>
    import {base} from "$app/paths"

    export let title = ""
    export let recipients = []

    let isSelected = false
    let dropdownIsOpen = false
    
    let inputWrapper
    let buttonImage
    let button

    function handleSelect() {
        isSelected = !isSelected
    }

    function handleDropdown() {
        dropdownIsOpen = !dropdownIsOpen
        buttonImage.style.backgroundImage = dropdownIsOpen ? `url('${base}/checkmark.png')` : `${base}/down.png`
    }
</script>


<div class="areaWrapper">
    <div bind:this={inputWrapper} 
    class="inputWrapper {isSelected ? "selected" : ""}">
        <label for="{title}">
            <input on:change={handleSelect} id="{title}" name="{title}" type="checkbox" />
            {title}
        </label>
    </div>

    {#if isSelected}
        <button bind:this={button} class="btn-dropdown" on:click={handleDropdown}>

            {dropdownIsOpen ? "Bestätigen" : "Personen auswählen"}

            <div bind:this={buttonImage} style="background-image: url('{base}/down.png');" 
            class="arrowDown"></div>
       
        </button>

        {#if dropdownIsOpen}
            <select id="{title}Select" name="{title}Select" multiple>
                {#each recipients as recipient}
                    <option value="{recipient}">{recipient}</option>
                {/each}
            </select>
        {/if}
    {/if}
</div>


<style>
    .arrowDown {
        background-position: center;
        background-repeat: no-repeat;
        background-size: contain;
        width: 1em; 
        height: 1em;
        transition: all .1s ease;
    }

    .btn-dropdown {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .selected {
        background: linear-gradient(90deg, skyblue, rgb(147, 175, 235));
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.363);
    }

    option {
        padding: 1em;
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
</style>