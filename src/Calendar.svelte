<script>
    import { onMount } from 'svelte';
    import { easepick } from '@easepick/bundle/dist/index.umd.js';

    let calendarElement;

    console.log(easepick);

    export let booked = [
        '2022-05-14', '2022-05-22',
        '2022-05-24', '2022-05-29',
        '2022-06-18', '2022-07-02',
        '2022-07-09', '2022-07-16',
        '2022-07-17', '2022-07-24',
        '2022-07-30', '2022-08-07',
        '2022-08-13', '2022-08-28'
    ];
    /*const bookedDates = booked.map(d => {*/
        /*if (d instanceof Array) {*/
            /*const start = easepick.DateTime(d[0], 'YYYY-MM-DD');*/
            /*const end = easepick.DateTime(d[1], 'YYYY-MM-DD');*/

            /*return [start, end];*/
        /*}*/

        /*return easepick.DateTime(d, 'YYYY-MM-DD');*/
    /*});*/

    onMount(() => {
        const picker = new easepick.create({
            element: calendarElement,
            css: [
                "https://cdn.jsdelivr.net/npm/@easepick/bundle@1.1.6/dist/index.css"
            ],
            zIndex: 10,
            lang: "fr-FR",
            /*format: "DD MMM YYYY",*/
            grid: 2,
            calendars: 2,
            inline: true,
            plugins: ['LockPlugin'],
            LockPlugin: {
                filter(date) {
                    return !booked.includes(date.format('YYYY-MM-DD'));
                },
            }
        })
        console.log(picker);
    });
</script>
<div bind:this={calendarElement}></div>
