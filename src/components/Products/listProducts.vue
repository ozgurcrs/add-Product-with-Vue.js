<template>
  <product>
    <div class="row product-container">
      <div v-for="(product,index) in products" :key="index" class="col-md-2 card">
        <img class="card-img-top" :src="product.selectedImage" alt="Card image cap" />
        <div class="card-body">
          <h5 class="card-title">{{product.title}}</h5>
          <small>
            <strong>Adet :</strong>
            {{product.count}}
          </small>
          <br />
          <small>
            <strong>Fiyat :</strong>
            {{product.price}}₺
          </small>
          <br />
          <small>
            <strong>Tutar :</strong>
            {{product.totalPrice}}₺
          </small>
        </div>
      </div>
    </div>
  </product>
</template>

<script>
import { eventBus } from "../../main";
import product from "./product";
export default {
  components: {
    product
  },
  data: () => {
    return {
      products: []
    };
  },

  created() {

        eventBus.$on("addedProduct", product => {
        if(this.products.length <2)
        {
            this.products.push(product);
            eventBus.$emit("countProducts", this.products.length);
            eventBus.$emit("nonEmpty", this.products.length);
        }
        else{
            alert("Kayıt Edilemez");
        }
      
       
      });
   
  }
};
</script>