<template>
    <div class="cartItem">
        <img class="cartItem__img" :src=" require('../assets/image/' + product_data.img) " alt="img">
        <h3>Модель: {{ product_data.name }}</h3>
        <p>Цена: {{ product_data.price }} руб</p>
        <p class="cartItem__description" >Описание:{{ product_data.discription }}</p>
        <button class="subscription__button" @click="addToBasket">Добавить в корзину</button>
    </div>
</template>
  
  <script>
  export default {
    name: 'vCart',
    components: {
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
        }
    },
    methods: {
        addToBasket() {
            this.$emit('add-to-basket',this.product_data)
        }
    }
  }
  </script>
  
  <style lang="scss">
    .cartItem {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 25%;
        box-shadow: 0 0 8px 0 #e0e0e0;
        padding: 16px;
        margin: 16px;
        &__img {
            max-width: 100%;
        }
        &__description {
            text-align: center;
        }
    }
  </style>