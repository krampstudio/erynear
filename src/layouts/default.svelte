<script>
    import 'modern-css-reset';
    import '../base.css';

    export let title;
    export let label;
    export let sideImages;

    $: hasSideImages = sideImages && sideImages.length;

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
        font-size: 4.5rem;
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
        background-color: rgba(255, 255, 255, 0.35);
        padding:.5rem 1rem;
        border-radius: 4px;
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
        background-color: rgba(255, 255, 255, 0.35);
        border-radius: 4px;
        list-style-type: none;
        display: flex;
        flex-flow: row wrap;
        justify-content: space-evenly;
        padding: 0;
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
        background-color: ivory;
    }
    main section {
        padding: 1rem;
        font-family: 'Dumbledor1';
        font-size: 1.35rem;
        letter-spacing: 0;
    }
    main section :global(p) {
        margin-bottom: 1rem;
    }
    main section :global(img) {
        max-width: 33vw;
        margin: .5rem;
        display: inline-block;
        vertical-align: top;
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

</style>

<svelte:head>
    <title>{title} {label}</title>
</svelte:head>

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

<footer></footer>
