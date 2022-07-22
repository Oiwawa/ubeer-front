<template>
  <div>
    <nav>
      <div class="nav-link">
        <a href="/" id="beer_link">Bières</a>
        <span class="bubble bubble1"></span>
        <span class="bubble bubble2"></span>
        <span class="bubble bubble3"></span>
        <span class="bubble bubble4"></span>
        <span class="bubble bubble5"></span>
        <span class="bubble bubble6"></span>
      </div>
      <img src="/assets/img/logo-ubeer.png" alt="logo ubeer">
      <div class="nav-link">
        <div id="cart_link">Panier</div>
        <span class="bubble bubble7"></span>
        <span class="bubble bubble8"></span>
        <span class="bubble bubble9"></span>
        <span class="bubble bubble10"></span>
        <span class="bubble bubble11"></span>
        <span class="bubble bubble12"></span>
      </div>
    </nav>
    <div class="beer_item">
      <h1>{{beer.name}}</h1>
      <p>{{beer.description}}</p>
      <p>Prix : <span>{{beer.price}} €</span></p>
      <p>Degré d'alcool : <span>{{beer.abv}} %</span></p>
      <p>Vendeur : <span>{{beer.seller.name}}</span></p>
    </div>
  </div>
</template>

<script setup>
const route = useRoute();
const beer = await $fetch('https://ubeer-back-hr.herokuapp.com/api/products/' + route.params.id).then(function (response) {
  return response
})
</script>
