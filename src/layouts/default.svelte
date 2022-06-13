<script>
    import { tick } from 'svelte';
    import { afterNavigate } from '$app/navigation';
    import ScrollButton from '../ScrollButton.svelte';
    import Gallerie from '../Gallerie.svelte';
    import 'modern-css-reset';
    import '../base.css';

    export let title;
    export let label;
    export let sideImages;

   $: hasSideImages = sideImages && sideImages.length;

    afterNavigate( async ({ from, to }) => {
        if( from !== null){
            await tick();
           document.querySelector('.content h2').scrollIntoView();
        }
    });
</script>
<style>
    header {
        max-width: 100vw;
        height: 100vh;
        position: relative;
        overflow: hidden;
        padding: 1rem 3rem;
        display: flex;
        flex-flow: column nowrap;

    }
    header h1, header h2, header h3, header h4, header nav {
        position: relative;
        z-index: 100;
    }
    header h1, header h2, header h3, header h4 {
        font-family: 'Traditian';
        text-shadow: 2px 2px 1px #ccc;
    }
    header h3, header h4 {
        font-family: 'Dumbledor1';
        text-shadow: 2px 2px 1px #ccc;
        letter-spacing: 0;
        text-align: center;
    }
    header h1 {
        font-size: 5rem;
        font-weight: bold;
        margin-bottom: 2rem;
    }
    header h2 {
        font-size: 3.25rem;
        margin-top: 3rem;
        text-align: center;
    }
    header h3 {
        font-size: 2rem;
    }
    header h4 {
        font-size: 2rem;
        margin: auto;
        background-color: rgba(255, 255, 255, 0.45);
        padding:.5rem 1rem;
        border-radius: 4px;
        box-shadow: 0 0 2px white;
    }

    header .separator {
        flex-grow:2;
    }
    header nav a{
        font-family: 'Dumbledor1';
        font-size: 1.75rem;
        font-weight: bold;
        color: #000;
    }
    header nav a:visited{
        color: #000;
    }
    header nav ul {
        background-color: rgba(255, 255, 255, 0.45);
        border-radius: 4px;
        list-style-type: none;
        display: flex;
        flex-flow: row wrap;
        justify-content: space-evenly;
        padding: 0;
        box-shadow: 0 0 2px white;
    }
    header nav ul li {
        padding: 0.5rem;
    }

    @media screen and (max-width: 1280px) {
        header {
            padding: 1rem 2rem;
        }

    }

    @media screen and (max-width: 1024px) {
        header h2 {
            font-size: 2.5rem;
        }
        header h3 {
            font-size: 1.75rem;
        }
    }

    @media screen and (max-width: 900px) {
        header h2 {
            text-align: center;
            font-size: 2rem;
        }
        header h3 {
            font-size: 1.5rem;
        }
        header h4 {
            display: none;
        }
    }

    @media screen and (max-height: 600px) {
        header h4 {
            display: none;
        }
    }

    @-webkit-keyframes slide {
        0% {margin-left: 0px;}
        28% {margin-left: 0px;}
        30% {margin-left: -100vw;}
        58% {margin-left: -100vw}
        60% {margin-left: -200vw;}
        88% {margin-left: -200vw;}
        90% {margin-left: -300vw;}
        100% {margin-left: -300vw;}
    }

    .carousel {
        z-index: 50;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;

    }
    .carousel .carousel-wrapper {
        position: relative;
        overflow: hidden;
        width: calc(400vw + 4rem);
        display: flex;
        flex-flow: row nowrap;
        animation: slide 60s ease infinite alternate;
    }
    .carousel .carousel-wrapper img {
        flex: 0 0 100vw;
        width: 100vw;
        height: 100vh;
        object-fit: cover;
    }

    main {
        display: flex;
        background-color: #fffff6 ;

        box-shadow: 0 0 125px #8f5922 inset;
        background: #fffef0;
        background-image: url('data:image/png;base64,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');
    }
    main section {
        padding: 2rem 3rem;
        font-family: 'Dumbledor1';
        font-size: 1.6rem;
        letter-spacing: 0;
        line-height: 1.3;
    }

    main section :global(p) {
        margin-bottom: 1rem;
    }
    main section :global(img) {
        max-width: 25vw;
        max-height: 250px;
        margin: .5rem;
        display: inline-block;
        vertical-align: top;
    }

    main section :global(h2) {
        font-size: .2.5rem;
        font-weight: bold;
        margin-bottom: 2rem;
    }
    main section :global(h3) {
        font-size: 2rem;
        display: flex;
        margin-bottom: 1.5rem;
    }
    main section :global(h3:before) {
        content: ' ';
        display: inline-block;
        width: 1.5em;
        height: 1.5em;
        background-image: url('/assets/crabe.png');
        background-size: 1.5em 1.5em;
        background-repeat: no-repeat;
        margin-right: 1rem;
    }
    main section :global(h4) {
        font-size: 1.6rem;
        margin-bottom: 1.25rem;
        font-weight: bold;
    }
    main section :global(h4:before) {
        content: '🙠 ';
        font-weight: bold;
    }

    main section :global(h5) {
        font-size: 1.6rem;
        margin-top: 0;
        margin-bottom: 1.25rem;
        font-weight: normal;
    }
    main section :global(h5:before) {
        content: '☸';
    }
    main section :global(a) {
        color: #000;
    }
    main section.with-side {
        width: 60%;
    }
    main aside {
        width: 40%;
        display: grid;
        grid-template-columns: 1fr 1fr;
    }

    main aside div img{
        height: 100%;
        object-fit: cover;
    }

    footer {
        min-height: 50vh;
        background-color: #111;
        color: white;
        text-align: center;
        padding-top: 10vh;
    }
</style>


  <ScrollButton />
  <header>
    <h1>Eryn Eär</h1>
    <nav>
        <ul>
            <li><a href="/">Accueil</a></li>
            <li><a href="/presentation">Les présentations</a></li>
            <li><a href="/gite">Le gîte</a></li>
            <li><a href="/alentour">Terres d’Eryn Ëar</a></li>
            <li><a href="/normandie">La Normandie</a></li>
            <li><a href="/glossaire">Glossaire</a></li>
            <li><a href="/reservations">Tarifs Réservations</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
    <h2>Gîte d'Eryn Eär en Normandie à Criel-sur-Mer</h2>
    <h3>Entre Forêts Millénaires et Mer Tumultueuse</h3>
    <div class="separator"></div>
    <h4>Explorer la nature - Découvrir la Normandie<br>
      Bouquiner – Jouer – se Défouler<br>
      S’évader - s’Oxygéner- se Ressourcer</h4>
    <div class="carousel">
        <div class="carousel-wrapper">
            <img src="/assets/home/1.jpg" alt="" />
            <img src="/assets/home/2.jpg" alt="" />
            <img src="/assets/home/3.jpg" alt="" />
            <img src="/assets/home/4.jpg" alt="" />
        </div>
    </div>
  </header>
  <main>
      <section class="content" class:with-side={hasSideImages}>
          <slot />
      </section>
      {#if hasSideImages}
          <aside>
            {#each sideImages as image}
                <div>
                    <img src={image} alt="" />
                </div>
            {/each}
          </aside>
      {/if}
  </main>

  <footer>
    <Gallerie />
  </footer>
