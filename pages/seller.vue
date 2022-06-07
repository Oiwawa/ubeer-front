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
    <div class="seller">
      <form name="addProduct" action="" method="POST" @submit="addProduct">
        <h1>Ajouter un produit</h1>
        <label for="name">Nom du produit</label>
        <input type="text" id="name" v-model="product_name" placeholder="Nom ...">
        <label for="description">Description du produit</label>
        <input type="text" id="description" v-model="description">
        <label for="price">Prix</label>
        <input type="number" id="price" v-model="price">
        <label for="abv">Degré d'alcool</label>
        <input type="number" id="abv" v-model="abv">
        <label for="seller_name">Votre nom</label>
        <input type="text" id="seller_name" v-model="seller_name">
        <label for="icon">Lien d'une image pour le produit</label>
        <input type="text" id="icon" v-model="icon">
        <input type="submit" value="Ajouter le produit" id="submit_button" />
      </form>
    </div>
  </div>
</template>
<script setup>
import {navigateTo} from "nuxt/app";

const product_name = ref('');
const description = ref('');
const price = ref('');
const abv = ref('');
const seller_name = ref('');
const icon = ref('');

async function addProduct() {
  let formData = new FormData();
  formData.append('name', product_name.value)
  formData.append('description', description.value)
  formData.append('price', price.value)
  formData.append('abv', abv.value)
  formData.append('seller_name', seller_name.value)
  formData.append('icon', icon.value)

  await $fetch('http://127.0.0.1:8000/api/product',
      {
        method: 'POST',
        body: formData,
      })
}
</script>
