
    <template>
      <div class="section">
        <div v-if="products.length > 0" class="shop">
      <li v-for="product in products" :key="product._id" @click="selectProduct(product)" :data-id="product.index" :class="product.isActive ? 'visible' : 'hidden'">
        <picture class="is-128x128">
          <img :src="product.picture" alt="Product Image">
        </picture>
        <h2>{{ product.name }}</h2>
      </li>
    </div>
  <ProductView :product="selectedProduct" v-if="selectedProduct" @productDeleted="handleProductDeleted" />
      </div>
  
</template>
    

<script setup>

import ProductView from '@/components/ProductView.vue';
import { ref, onBeforeMount } from 'vue';

const selectedProduct = ref(null);

const selectProduct = (product) => {
  selectedProduct.value = product;
};

const handleProductDeleted = (deletedProduct) => {
  console.log(`Product deleted: ${deletedProduct.name}`);
  // alert(`${deletedProduct.name} parent`);

  selectedProduct.value.isActive = false;
  // alert(`${selectedProduct.value.name}'s isActive: ${selectedProduct.value.isActive}`);
};

const products = ref([]);

onBeforeMount(() => {
  fetch("/product.json")
    .then(res => res.json())
    .then(res => {
      products.value = res;
    })
    .catch(error => console.log(error));
});


</script>

