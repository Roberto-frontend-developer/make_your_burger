<template>
  <Banner />
  <div class="main-container">
    <h1>Escolha seu burger</h1>
    <BurgerFom />
  </div>
</template>
<script>
import Banner from "../components/Banner.vue";
import BurgerFom from "../components/BurgerFom.vue";

export default {
  name: "Homer",
  components: {
    Banner,
    BurgerFom,
  },
};
</script>
