<script>
    export let weekHigh = 490;
    export let weekLow = 380;
    export let weekendFamily = 200;
    export let weekendFriends = 250;

</script>
<style>

    table {
        width:80%;
        margin: auto;
        border-collapse: collapse;
        border: solid 1px black;
    }
    table thead th {
        background-color: lightblue;
    }
    table th,
    table td {
        border: solid 1px black;
        padding: .5rem;
    }

</style>
<table>
    <thead>
        <tr>
            <th colspan="2">Le Gîte entier : FORMULES 2022-2023</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<strong><em>Otsola</em> (semaine), soit 8 jours et 7 nuits</strong>

<ul>
    <li>du samedi 16h au samedi suivant 11h</li>
    <li>ou jour d’arrivée/départ et horaires adaptables en fonction des disponibilités.</li>
</ul>
Haute saison de début juin à fin septembre : <strong>{weekHigh}€</strong>
<br>
Basse saison mi mars-avril-mai et octobre : <strong>{weekLow}€</strong>
            </td>
            <td>
<strong><em>Tyel Otsola</em> (week-end) selon disponibilités</strong>
<ul>
    <li>Du vendredi au dimanche</li>
    <li>Haute et basse saison</li>
</ul>
2 à 4 personnes : <strong>{weekendFamily}€</strong>
<br>
5 à 10 personnes : <strong>{weekendFriends}€</strong>
            </td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th colspan="2">

Pensez à apporter vos draps et linge de maison (serviettes de toilette, chiffons).

Animaux non admis pour le moment

            </th>
        </tr>
    </tfoot>
</table>
