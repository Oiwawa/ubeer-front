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
      <p>{{beer.name}}</p>
      <p>{{beer.description}}</p>
      <p>{{beer.price}} €</p>
      <p>{{beer.abv}} %</p>
      <p>{{beer.seller.name}}</p>
    </div>
  </div>
</template>

<script setup>
const route = useRoute();
const beer = await $fetch('http://127.0.0.1:8000/api/product/' + route.params.id).then(function (response) {
  return response
})
</script>
