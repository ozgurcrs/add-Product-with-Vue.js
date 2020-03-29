<template>
  <div class="container">
    <h1 class="text-center">Ürün Ekleme Uygulaması</h1>
    <hr />
    <addProduct />
    <br />
    <br />
    <progressBar />
    <br />
    <br />
    <h3 v-if="showList" class="text-center">Eklenen Ürünlerin Listesi</h3>
    <hr />
    <listProducts />
  </div>
</template>

<script>
import { eventBus } from "./main";
import addProduct from "./components/Products/addProduct";
import listProducts from "./components/Products/listProducts";
import progressBar from "./components/progressBar";
export default {
  components: {
    addProduct,
    listProducts,
    progressBar
  },

  data: () => {
    return {
      showList: false
    };
  },

  created() {
    eventBus.$on("nonEmpty", nonEmpty => {
      if (nonEmpty > 0) {
        this.showList = true;
      }
    });
  }
};
</script>

<style>
body {
  background-color: aliceblue;
  padding-top: 20px;
  padding-bottom: 20px;
}

.card {
  margin-right: 5px;
  margin-bottom: 5px;
}

.card:last-child {
  margin-right: 0px;
}

.col-md-2 {
  max-width: 15.666667% !important;
}

.product-container {
  margin-left: 15px;
}
</style>

