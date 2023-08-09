<script>
    import {base} from "$app/paths"
</script>


<header>
    <div>
        <h1>Abwesenheits-Melder</h1>
        <div class="account" style="background-image: url('{base}/account.png');"></div>
    </div>
</header>


<style>
    header {
        width: 100%;
    }

    header > div {
        max-width: 750px;
        padding: 1em 2em;
        margin: auto;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    h1 {
        font-weight: bold;
        letter-spacing: 3px;
        margin: 0;
        font-size: 1.2em;
        text-align: center;
    }

    .account {
        width: 40px;
        height: 40px;
        background-repeat: no-repeat;
        background-position: center;
        background-size: contain;
        border-radius: 100%;
        transition: all .1s ease;
        cursor: pointer;
        position: relative;
    }

    .account::after {
        position: absolute;
        content: '';
        right: 0;
        top: 0;
        width: 0;
        height: 0;
        border-radius: 100%;
        box-shadow: 0 0 0 3px black;
        z-index: -3;
        transition: all .1s ease;
        opacity: 0;
    }

    .account:hover {
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.281);
    }

    .account:hover::after {
        width: 100%;
        height: 100%;
        opacity: 1;
    }
</style>