<script>
    import { onMount } from 'svelte';
    import flatpickr from "flatpickr";
    import 'flatpickr/dist/flatpickr.css';

    let calendarElement;

    export let booked = [
        { from: '2022-05-14', to: '2022-05-22'},
        { from: '2022-05-24', to: '2022-05-29'},
        { from: '2022-06-18', to: '2022-07-02'},
        { from: '2022-07-09', to: '2022-07-16'},
        { from: '2022-07-17', to: '2022-07-24'},
        { from: '2022-07-30', to: '2022-08-07'},
        { from: '2022-08-13', to: '2022-08-28'}
    ];
    export let maxDate = '2022-12-15';

    onMount(() => {
        const calendar =  flatpickr(calendarElement, { inline: true, disable: booked, minDate: new Date(), maxDate, showMonths: 2, position: 'auto center'});
    });
</script>
<style>
    :global(.flatpickr-calendar) {
        margin: auto;
    }
    :global(.flatpickr-day){
        color: black;
        background-color: #bbdba9;
    }
</style>
<div bind:this={calendarElement}></div>
