<template>
  <body>
    <div class="map--container">
      <h2>Mais où se trouve donc Wilson ?</h2>
      <p>Affiche les deux adresses de l'agence Ylly : Lille et Paris ! </p>
      <p>Consigne suivante : Savoir choisir entre Lille ou paris (formulaire) // Barre de recherche </p>
      <iframe class="map--iframe" src="https://www.google.com/maps/d/u/0/embed?mid=10mgQUxVCBhSATcTkhWaV51bhLdmQ3CoD" width="1300" height="500px"></iframe>
    </div>
  </body>
</template>

<script>

</script>

<style>

  body {
    background: #4D6A79;
  }
  .map--container {
    text-align: center;
    color: whitesmoke;
  }

  .map--iframe {
    border: 0.2rem whitesmoke solid;
    border-radius: 0.5rem;
  }

 .map {
   position: absolute;
   width: 100%;
   height: 100%;
   overflow :hidden;
 }
</style>