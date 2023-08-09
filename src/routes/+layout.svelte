<script>
    import Header from "../lib/global/Header.svelte";

</script>

<Header />


<div class="bg"></div>

<div class="mainContainer">
    <main>
        <slot>
    
        </slot>
    </main>
</div>



<style>
    .bg {
        position: absolute;
        inset: 0;
        background: radial-gradient(white, rgb(159, 188, 207));
        z-index: -10;
        pointer-events: none;
        opacity: .3;
    }

    .mainContainer {
        max-width: 800px;
        margin: auto;
    }

    main {
        padding: 1.5em 8px;
        margin: auto;
        background: white;
        margin: 0 8px;
        border-radius: .5em;
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.178);
    }
</style>