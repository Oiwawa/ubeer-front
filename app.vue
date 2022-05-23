<template>
  <div>
    <nav>
      <div class="nav-link">
        <div id="beer_link">Bières</div>
        <span class="bubble bubble1"></span>
        <span class="bubble bubble2"></span>
        <span class="bubble bubble3"></span>
        <span class="bubble bubble4"></span>
        <span class="bubble bubble5"></span>
        <span class="bubble bubble6"></span>
      </div>
      <img src="assets/img/logo-ubeer.png" alt="logo ubeer">
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
    <div class="content">
      <form action="" class="filters">
        <details>
          <summary>Toutes les brasseries</summary>
          <ul>
            <li>Lorem ipsum</li>
            <li>Lorem ipsum</li>
            <li>Lorem ipsum</li>
          </ul>
        </details>
        <input type="text" placeholder="Mots-clés">
        <button>Chercher</button>
      </form>
      <div class="beer-grid" v-for="beer in beers">
        <div class="beer-card">
          <img src="assets/img/biere3.png" alt="biere" class="beer_img">
          <div class="add-cart">
            <img src="assets/img/add-to-cart.png" alt="ajout panier">
            <p class="count_nb_item">
              <span class="less_item">-</span>
              <span class="nb_item"></span>
              <span class="more_item">+</span>
            </p>
          </div>
          <p class="beer_name">{{beer.name}}</p>
          <p class="brewery">{{ beer.seller.name }}</p>
        </div>
      </div>
    </div>
    <div id="cart_modal">
      <div class="modal-header">
        <span id="close_modal">X</span>
        <h2>Panier</h2>
        <a href="#" id="pay_link">Payer</a>
      </div>
      <div id="cart_content"></div>
    </div>
  </div>
</template>

<script setup>

const beers = await $fetch('http://127.0.0.1:8000/api/product').then(function() {
  return response
})
</script>
