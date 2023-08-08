<script>
    import Header from "../lib/Header.svelte";

</script>


<Header />

<main>
    <slot>

    </slot>
</main>


<style>
    main {
        padding: 2em 8px;
        margin: auto;
        background: white;
        max-width: 800px;
    }
</style>