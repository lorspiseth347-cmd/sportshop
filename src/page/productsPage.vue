<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary sticky-top shadow">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"
        ><h2><i class="bi bi-shop"></i> SPORTSHOP</h2></a
      >
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarScroll"
        aria-controls="navbarScroll"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarScroll">
        <ul
          class="navbar-nav me-auto my-2 my-lg-0 navbar-nav-scroll"
          style="--bs-scroll-height: 100px"
        >
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">About</a>
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              Brand
            </a>
            <ul class="dropdown-menu">
              <li><a class="dropdown-item" href="#">NIKE</a></li>
              <li><a class="dropdown-item" href="#">ADIDA</a></li>
            </ul>
          </li>
        </ul>
        <form class="d-flex" role="search">
          <input
            class="form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <div>
            <!-- Button trigger modal -->
            <div
              type="button"
              data-bs-toggle="modal"
              data-bs-target="#exampleModal"
            >
              <!-- <i class="bi bi-person-fill"></i> -->
              <i class="bi bi-person-fill fs-3 me-2"></i>
            </div>

            <!-- Modal -->
          </div>
          <Cart :items="cart" />
        </form>
      </div>
    </div>
  </nav>
  <div class="container mt-2">
    <img
    class="w-100"
      src="https://i.pinimg.com/736x/0e/83/83/0e83836aa3943ada915dfb3c80ddb4e9.jpg"
      alt=""
    />
  </div>
   <h1 class="mt-3 container fw-bold">NIKE</h1>

  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="exampleModalLabel">Modal title</h1>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">...</div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Close
          </button>
          <button type="button" class="btn btn-primary">Save changes</button>
        </div>
      </div>
    </div>
  </div>

  <div class="container mt-4">
    <div class="row">
      <div
        v-for="product in Products"
        :key="product.id"
        class="col-12 col-md-6 col-lg-3 mt-3"
      >
        <ProductCard @add-to-cart="getProduct" :product="product" />
      </div>

      <div class="container">
        <h1 class="mt-3 fw-bold">ADIDAS</h1>
        <div class="row">
          <div
            v-for="product in Productss"
            :key="product.id"
            class="col-12 col-md-6 col-lg-3 mt-3"
          >
            <ProductCard @add-to-cart="getProduct" :product="product" />
          </div>
        </div>
      </div>

      <div>
        <h1 class="mt-3 fw-bold">Mizuno</h1>
        <div class="row">
          <div
            v-for="product in Productsss"
            :key="product.id"
            class="col-12 col-md-6 col-lg-3 mt-3"
          >
            <ProductCard @add-to-cart="getProduct" :product="product" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import Cart from "../components/cart.vue";
// import Cart from "../components/cart.vue";
import ProductCard from "../components/productCard.vue";
import { Products, Productss, Productsss } from "../data/ProductData.js";
import type { Product } from "../type/products.ts";

const cart = ref<Product[]>([]);

function getProduct(data: Product) {
  cart.value.push(data);
}
</script>
