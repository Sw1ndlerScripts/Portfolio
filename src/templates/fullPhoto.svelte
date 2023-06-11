<script>
    export let photo;
</script>

<style>
    .image-background {
        width: 100vw;
        height: 100vh;

        background-color: black;

        opacity: 30%;
        position: fixed;

        z-index: -1;
    }

    .image-wrapper {
        width: 100vw;
        height: 100vh;

        display: flex;
        justify-content: center;
        align-items: center;

        z-index: 5;
        position: fixed;
    }

    .image-container {
        width: 45%;
        height: 45%;
    }

    .image {
        width: 100%;
        height: 100%;

        object-fit: contain;
    }
</style>



<div class='image-wrapper'>
    <div class='image-background'></div>

    <div class='image-container'>
        <img class='image' alt='' src='{photo}' />
    </div>
</div>
