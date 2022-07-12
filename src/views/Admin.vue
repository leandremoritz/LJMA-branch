<template>
  <div class="display">
    <card v-for="product in products" :key="product.id" :product="product" />
  </div>
</template>
<script>
import Card from "@/components/Card.vue";
export default {
  components: { Card },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    fetch(" http://localhost:3000/products")
      .then((res) => res.json())
      .then((data) => (this.products = data))
      .catch((err) => console.log(err.message));
  },
};
</script>
<style scoped>
.display {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-content: center;
  gap: 25px;
}
</style>
