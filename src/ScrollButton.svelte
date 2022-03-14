<script>
    import { onMount } from 'svelte';
    export let direction = 'down'

    let anchor;
    let y;

    onMount(() => anchor = document.querySelector('.content h2'));
    function scroll(){
        if(direction === 'up') {
            window.scrollTo(0, 0);
        }else if(direction === 'down' && anchor){
            anchor.scrollIntoView();
        }
    }
    $: direction = y > 0 ? 'up' : 'down';
</script>
<style>
    button {
        position: fixed;
        bottom: 2rem;
        right: 2rem;
        width: 3rem;
        height: 3rem;
        color: black;
        background-color: white;
        border: solid 2px black;
        border-radius: 5px;
        z-index: 10000;
        font-size:1.5rem;
        opacity: .65;
        box-shadow: 0 0 2px grey;
    }
    button:hover {
        opacity: .85;
        cursor: pointer;
    }
    @media screen and (max-width: 900px) {
        button {
            display: none;
        }
    }
</style>
<svelte:window bind:scrollY={y} />
<button name="scroll-to" data-direction={direction} aria-label="scroll {direction}" on:click={scroll}>
    {#if direction === 'down'}
        🢃
    {:else}
        🢁
    {/if}
</button>
