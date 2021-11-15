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
        padding: 1rem 2rem;
        display: flex;
        flex-flow: column nowrap;
    }
    header h1, header h2, header h3, header h4, header nav {
        position: relative;
        z-index: 100;
    }
    header h1, header h2, header h3, header h4 {
        font-family: 'Traditian';
        text-shadow: 1px 1px 1px #aaa;
    }
    header h3, header h4 {
        font-family: 'Dumbledor1';
        text-shadow: 1px 1px 1px #aaa;
        letter-spacing: 0;
    }
    header h1 {
        font-size: 5rem;
        font-weight: bold;
    }
    header h2 {
        font-size: 3rem;
    }
    header h3 {
        font-size: 2rem;
    }
    header h4 {
        font-size: 2rem;
    }
    header h3, header h4{
        text-align: center;
    }
    .separator {
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
        background-color: rgba(255, 255, 255, 0.1);
        border-radius: 3px;
        list-style-type: none;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-around;
        padding:0;
    }
    .carousel {
        z-index: 50;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        overflow: hidden;
    }
    .carousel img {
        width: 100%;
        object-fit: cover;
    }
    main {
        display: flex;
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
        <img src="/assets/home/1.jpg" alt="" />
        <img src="/assets/home/2.jpg" alt="" />
        <img src="/assets/home/3.jpg" alt="" />
        <img src="/assets/home/4.jpg" alt="" />
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
