<template>
  <section>
    <h2>{{ title }}</h2>
    <h3>${{ price }}</h3>
    <p>{{ description }}</p>
  </section>
</template>

<script>
import { inject } from 'vue';
import { useRoute } from 'vue-router';

export default {
  props: ['pid'],
  setup(props) {
    const route = useRoute();
    const products = inject('products');

    // other way to get pid
    console.log(route.params.pid);

    const selectedProduct = products.value.find(
      (prod) => prod.id === props.pid
    );
    const title = selectedProduct.title;
    const price = selectedProduct.price;
    const description = selectedProduct.description;

    return { title, price, description };
  },
};
</script>

<style scoped>
section {
  margin: 3rem auto;
  max-width: 40rem;
  padding: 1rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
}
</style>
