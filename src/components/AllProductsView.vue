<template>
  <li @click="handleClick" :data-id="product.index" v-show="product.isActive">
    <picture class="is-128x128">
      <img :src="product.picture" alt="Product Image">
    </picture>
    <h2>{{ product.name }}</h2>
  </li>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps(['product', 'click']);

const handleClick = () => {
  props.click(props.product);
};
</script>
