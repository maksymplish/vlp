<template>
  <div id="app">
    <h1 class="text-center">Усі видання</h1>
    <div class="row align-center">
      <div class="column small-12 medium-10">
        <div class="flex-container align-justify">
          <Pagination :totalPages="getTotalPages()" />

          <select v-model="itemsPerPage" class="small-2">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="8">8</option>
            <option value="12">12</option>
          </select>
        </div>
        <hr />
      </div>
    </div>
    <div class="row">
      <div
        class="column small-12 medium-6 large-3"
        v-for="book, index in products"
        v-if="index < itemsPerPage"
      >
        <article class="ba-poduct">
          <a :href="book.url">
            <img :src="book.img" :alt="book.title" />
          </a>
          <h3 class="ba-poduct__title">{{book.title}}</h3>
          <p class="ba-producr__author">{{book.authors}}</p>
          <div class="ba-price">{{book.price}}</div>
        </article>
      </div>
    </div>
    <div class="row align-center">
      <div class="column small-12 medium-6">
        <Pagination :totalPages="getTotalPages()" />
        <hr />
      </div>
    </div>
  </div>
</template>

<script>
// import json from '../db/book.json';

import Pagination from "./components/Pagination.vue";

export default {
  data() {
    return {
      itemsPerPage: 8,
      products: []
    };
  },
  methods: {
    getTotalPages() {
      return Math.ceil(this.products.length / this.itemsPerPage);
    }
  },
  mounted() {
    fetch("assets/db/book.json")
      .then(res => res.json())
      .then(list => (this.products = list));
  },
  components: {
    Pagination
  }
};
</script>
