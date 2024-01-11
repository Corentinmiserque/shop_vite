<template>
  <div class="product" v-if="product" v-show =" product.isActive"  >
    <h2>{{ product.name }}</h2>
    <p>{{ product.about }}</p>
    <p>Price: {{ product.price }}</p>
    <p :style="{ color: product.color }">Color: {{ product.color }}</p>
    <p>Categorie: {{ product.categorie }}</p>
    <picture class="is-128x128">
        <img :src="product.picture" alt="Product Image">
      </picture>

      <button @click="toggleVisibility">Delete</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';


const props = defineProps({
  product: {
    type: Array, 
    default: () => ([]) 
  }
});
const emits = defineEmits({
  productDeleted:{
    type: Array, 
    default: () => ([]) 
  }
});

const toggleVisibility = () => {

  // alert(`${props.product.name} is active = ${props.product.isActive}`);
  emits('productDeleted', props.product);

};
</script>


