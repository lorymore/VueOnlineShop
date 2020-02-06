<template>
  <div class="v-catalog-item">

    <v-popup
      v-if="isInfoPopupVisible"
      leftBtnTitle="Add to Cart"
      :popupTitle="product_data.name"
      @closePopup="closeInfoPopup"
      @leftBtnAction="addToCart"
    >
    <img class="v-catalog-item__image" :src=" require('../../assets/images/'+ product_data.image)" alt="">
    <div>
      <p class="v-catalog-item__name">{{product_data.name}}</p>
      <p class="v-catalog-item__price">Price: {{product_data.price}}  &#8381;</p>
      <p class="v-catalog-item__price">{{product_data.category}}</p>
    </div>
    </v-popup>

    <img class="v-catalog-item__image" :src=" require('../../assets/images/'+ product_data.image)" alt="">
    <p class="v-catalog-item__name">{{product_data.name}}</p>
    <p class="v-catalog-item__price">Price: {{product_data.price}}  &#8381;</p>
    <button
      class="v-catalog-item__show_info btn"
      @click="showPopupInfo"
    >
      Show Info
    </button>
    <button 
    class="v-catalog-item__add_to_cart_btn btn" 
    @click="addToCart"
    >Add to cart
    </button>
  </div>
</template>

<script>
import vPopup from '../popup/v-popup'

export default {
  name: "v-catalog-item",
  components: {
    vPopup
  },
  props: {
    product_data: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  data() {
    return {
      isInfoPopupVisible: false
     }
  },
  computed: {},
  methods: {
    showPopupInfo() {
      this.isInfoPopupVisible = true;
    },
    closeInfoPopup() {
      this.isInfoPopupVisible = false;
    },
    addToCart(){
      this.$emit('addToCart',this.product_data);
    }
  },
}
</script>

<style lang="scss">
  .v-catalog-item {
    flex-basis: 25%;
    box-shadow: 0 0 8px #e0e0e0;
    padding: $padding*2;
    margin-bottom: $margin*2;
    &__image {
      width: 120px;
    }
    &__show_info {
      margin-right: 4px;
    }
  }
</style>