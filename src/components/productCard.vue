<!-- <template>
  

  <div class="card" style="width: 18rem">
    <img :src="product.images" class="card-img-top" alt="..." />
    <div class="card-body">
      <h5 class="card-title">{{ product.title }}</h5>
      <h5 class="card-title">{{ product.price }}</h5>
      <div class="d-flex justify-content-between">
        <a href="#" class="btn btn-primary"></a>
        <p>Stock:{{ product.stock }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// import { ref } from "vue";
// import type { Product } from "../type/products";
import { Product } from "../type/products";

let props = defineProps<{
  product: Product;
}>();
</script> -->

<!-- <template>
  <div>
   
    
    <div class="card h-100" style="width: 18rem;">
      <img 
        :src="product.images" 
        class="card-img-top" 
        :alt="product.title" 
      />
      <div class="card-body d-flex flex-column justify-content-between">
        <div>
          <h5 class="card-title">{{ product.title }}</h5>
          <p class="card-text text-primary fw-bold">${{ product.price }}</p>
        </div>
        <div class="d-flex justify-content-between align-items-center mt-3">
          <a href="#" class="btn btn-primary">Add to Cart</a>
          <span class="badge bg-secondary">Stock: {{ product.stock }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// Import interface using 'import type' keyword
import type { Product } from "../type/products";

// Define typed props
defineProps<{
  product: Product;
}>();
</script> -->

<template>
  <!-- h-100 ដើម្បីឱ្យ Card ទាំងអស់ពង្រីកកម្ពស់ពេញ Column -->
  <div class="card w-100 h-100 shadow-sm border-light-subtle">
    <!-- រូបភាពកំណត់កម្ពស់ថេរ -->
    <img
      :src="product.images"
      class="card-img-top object-fit-contain bg-light"
      :alt="product.title"
    />

    <!-- d-flex flex-column justify-content-between ช่วย push button ទៅបាតក្រោមស្មើគ្នា -->
    <div class="card-body d-flex flex-column justify-content-between p-3">
      <div>
        <!-- កំណត់កម្ពស់អប្បបរមា (min-height) សម្រាប់ Title ដើម្បីឱ្យស្មើគ្នាទោះចំណងជើងខ្លីឬវែង -->
        <h6
          class="card-title fw-bold text-dark mb-2"
          style="max-height: 2rem"
        >
          {{ product.title }}
        </h6>
        <p class="card-text text-primary fw-bold mb-0">
          {{ product.price }}
        </p>
      </div>

      <!-- ផ្នែក Button & Stock នៅបាតក្រោម -->
      <div
        class="d-flex justify-content-between align-items-center mt-3 pt-2 border-top"
      >
        <button
          @click="handleAdd"
          :disabled="product.stock === 0"
          class="btn btn-primary btn-sm px-2"
        >
          {{ product.stock === 0 ? "Out of stock" : "Add to cart" }}
        </button>
        <span class="badge bg-secondary">Stock: {{ product.stock }}</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Product } from "../type/products";

const props = defineProps<{
  product: Product;
}>();

const emit = defineEmits<{
  "add-to-cart": [Product: Product];
}>();

function handleAdd() {
  emit("add-to-cart", props.product);
}
</script>
