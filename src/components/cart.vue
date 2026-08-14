<script setup lang="ts">
import type { Product } from "../type/products";

defineProps<{
  items: Product[];
}>();
</script>

<template>
  <!-- 1. BUTTON STAYS IN NAVBAR -->
  <div
   class="me-3"
    data-bs-toggle="offcanvas"
    data-bs-target="#cartOffcanvas"
    aria-controls="cartOffcanvas"
  >
    <i class="bi bi-cart2 fs-3"></i>
    <span
      v-if="items.length > 0"
      class="position-absolute mt-2 translate-middle badge rounded-pill bg-danger me-4"
    >
      {{ items.length }}
    </span>
  </div>

  <!-- 2. DRAWER IS TELEPORTED DIRECTLY TO THE <body> TAG -->
  <Teleport to="body">
    <div
      class="offcanvas offcanvas-start"
      data-bs-scroll="true"
      tabindex="-1"
      id="cartOffcanvas"
      aria-labelledby="cartOffcanvasLabel"
    >
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="cartOffcanvasLabel">
          Your Shopping Cart
        </h5>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="offcanvas"
          aria-label="Close"
        ></button>
      </div>

      <div class="offcanvas-body">
        <!-- Empty state message -->
        <p v-if="items.length === 0" class="text-muted text-center my-4">
          Your cart is empty.
        </p>

        <!-- Loop items -->

        <div v-for="item in items" :key="item.id" class="card mb-3 shadow-sm">
          <div class="d-flex justify-content-between align-items-center p-2">
            <div class="d-flex align-items-center">
              <img
                :src="item.images"
                style="width: 80px; height: 80px; object-fit: contain"
                class="p-1"
                :alt="item.title"
              />
              <div class="ms-3">
                <h6 class="card-title mb-1 fw-bold">{{ item.title }}</h6>
                <p class="card-text text-muted mb-0">{{ item.price }}</p>
              </div>
            </div>
            <button
              class="btn btn-outline-danger btn-sm me-2"
              title="Remove item"
            >
              <i class="bi bi-trash"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
  </Teleport>
</template>
