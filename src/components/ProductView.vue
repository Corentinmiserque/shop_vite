<template>
  <div class="product" v-if="product">
    <h2>{{ product.name }}</h2>
    <p>{{ product.about }}</p>
    <p>Price: {{ product.price }}</p>
    <p>Color: {{ product.color }}</p>
    <p>Categorie: {{ product.categorie }}</p>
    <picture class="is-128x128">
        <img :src="product.picture" alt="Product Image">
      </picture>

      <button @click="toggleVisibility">Toggle Visibility</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['product']);
const emits = defineEmits(['productDeleted']);

const toggleVisibility = () => {

  props.product.isActive = false;
  alert(`${props.product.name} is active = ${props.product.isActive}`);

  emits('productDeleted', props.product);

};
</script>


