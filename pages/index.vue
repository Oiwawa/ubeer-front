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
      <img src="../assets/img/logo-ubeer.png" alt="logo ubeer">
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
        <select>
          <option>Toutes les brasseries</option>
          <option v-for="seller in sellers">{{seller.name}}</option>
        </select>
        <input type="text" placeholder="Mots-clés">
        <button>Chercher</button>
      </form>
      <div class="beer-grid">
        <div class="beer-card" v-for="beer in beers" :key="beer.id">
          <NuxtLink :to="'/beers/' + beer.id" class="beer_name">
           <img :src='beer.icon' alt="biere" class="beer_img">
          </NuxtLink>
          <div class="add-cart">
            <img src="../assets/img/add-to-cart.png" alt="ajout panier">
            <p class="count_nb_item">
              <span class="less_item">-</span>
              <span class="nb_item"></span>
              <span class="more_item">+</span>
            </p>
          </div>
          <p class="beer_name">{{beer.name}}</p>
          <p class="beer_name">{{beer.price}} € </p>
          <NuxtLink :to="'/sellers/' + beer.seller.id" class="brewery">
            <p >{{ beer.seller.name }}</p>
          </NuxtLink>

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

    <div class="seller_link">
      <a href="/seller" id="seller_link">Ajouter un produit</a>
    </div>
  </div>
</template>

<script setup>
const beers = await $fetch('https://ubeer-back-hr.herokuapp.com/api/products').then(function(response) {
  return response
})

const sellers = await $fetch('https://ubeer-back-hr.herokuapp.com/api/sellers').then(function (response) {
  return response;
})
</script>
