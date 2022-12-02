<template>
    <div id="catalogTop">
        <h1 class="h1">Каталог</h1>
        <div class="catalog">
            <vCart 
            v-for="product in products"
            :key="product.name"
            :product_data="product"
            @add-to-basket="addToBasket"
            />
        </div> 
        <h2 class="h1">Корзина</h2>
        <div class="bascet" v-if="(basket.length > 0)">
            <div class="bascet-box">
                <div class="bascet-box__items">
                    <div class="bascet-box__name" v-if="(basket.length > 0)">
                        <p class="text" >Товаров в корзине: {{ basket.length }}</p>
                        <button class="subscription__button" @click="clearBasket">Очистить корзину</button>
                    </div>
                    <div class="cartBasket"
                    v-for="item in basket"
                    :key="item.id">
                        <img class="cartBasket-img" :src=" require('../assets/image/' + item.img) " alt="img">
                        <div class="cartBasket__content">
                            <p class="content__h3"> {{ item.name }} </p> 
                            <p class="content__description"> {{ item.discription }} </p>
                            <p class="content__price__sell"> Цена: {{ item.price }}</p>
                        </div>
                        <button class="bascet-form__button-smal" @click="clearCart(item.id)">X</button>
                    </div>
                </div>
            </div>
            <div class="bascet-form">
                <p class="bascet-form__text">Оформление заказа</p>
                <div class="form-box">
                    <input type="text" placeholder="Имя Фамилия" class="form-input">
                    <input type="tel" placeholder="+ 7 904 000 80 80" class="form-input">
                    <input type="text" placeholder="Адрес доставки" class="form-input">
                </div>
                <p class="bascet-form__text">Итого: {{ allPrice }}</p> 
                <button class="bascet-form__button">Оформить заказ</button>
            </div>
        </div>
    </div>
  </template>
  
<script>
import vCart from '../components/cart.vue'

export default {
  name: 'vCatalog',
  components: {
    vCart
  },
  data() {
    return {
        products: [
                {
                    img: "taran.jpg",
                    name: "Кровать TATRAN",
                    price: 120000,
                    discription: "Основание из полированной нержавеющей стали, придает оригинальный парящий эффект.",
                    id: "1",
                    basket: false
                },
                {
                    img: "product1.jpg",
                    name: "Кресло VILORA",
                    price: 21000,
                    discription: "Мягкое и уютное, аккуратное и стильное. Упругие подушки сиденья и приятная на ощупь ткань.",
                    id: "2",
                    basket: false
                },
                {
                    img: "menutable.jpg",
                    name: "Стол MENU",
                    price: 34000,
                    discription: "Для того чтобы трапезничать было приятно, необходим правильный обеденный стол.",
                    id: "3",
                    basket: false
                },
                {
                    img: "askesta.jpg",
                    name: "Кресло ASKESTA",
                    price: 68000,
                    discription: "Высокоэластичный пенополиуретан в «начинке» кресла надежен и долговечен",
                    id: "4",
                    basket: false
                },
                {
                    img: "normantable.jpg",
                    name: "Стол NORMAN",
                    price: 40000,
                    discription: "Прекрасно переносит солнечные лучи, перепады влажности и любые осадки",
                    id: "5",
                    basket: false
                },
                {
                    img: "nastan.jpg",
                    name: "Диван NASTAN",
                    price: 80000,
                    discription: "Модель отличается простотой линий и форм, отсутствием броского декора.",
                    id: "6",
                    basket: false
                }
            ],
        basket: []
    }
  },
  methods: {
        saveLocalStorage () {
            localStorage.setItem("basket",JSON.stringify(this.basket))
        },
        addToBasket(product_data) {
            this.basket.push(product_data)

            this.saveLocalStorage () 
        },
        clearCart(id) {
            for (let index = 0; index < this.basket.length; index++) {
                const cart_item = this.basket[index].id

                if  (cart_item === id) {
                    this.basket.splice(index,1)
                    for (let i = 0;  i < this.products.length; i++) {
                        if (cart_item == this.products[index].id) {
                            this.products[i].basket = false

                            this.saveLocalStorage()
                        }
                    }
                }

                let cartLocalStorage = JSON.parse(localStorage.getItem("basket"))
                if (cartLocalStorage.length == 0) {
                    localStorage.removeItem("basket")
                }
            }
        },
        clearBasket() {
            this.basket = []

            localStorage.removeItem("basket")
            for (let i = 0; i < this.products.length; i++) {
                this.products[i].basket = false
            }
        },
        cartLocalStorage() {
            if (localStorage.getItem("basket")) {
                let cartLocalStorage = JSON.parse(localStorage.getItem("basket"))
                console.log(cartLocalStorage);
                return cartLocalStorage}
                else {return []}
        },
    },
  computed: {
    allPrice () {
        let price = 0
        for (let index = 0; index < this.basket.length; index++) {
            price += this.basket[index].price 
        }
        return price
    }
  }
}

</script>
  
<style lang="scss"> 
    .h1 {
        font-weight: 600;
        font-size: 30px;
    }
    .catalog {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-evenly;
    }
    .bascet {
        margin: 64px;
        display: flex;
        gap: 32px;
        &-box {  
            border-bottom: 0.5px solid #CACDD8;     
            border-top: 0.5px solid #CACDD8;     
            &__name {
                margin-bottom: 30px;
                display: flex;
                justify-content: space-between;
                align-items: center;
            }
            &__items {
                display: flex;
                flex-direction: column;
                padding-top: 25px;
                padding-bottom: 32px;               
                &-text {
                    display: flex;
                    align-items: center;
                    flex-wrap: wrap;
                    justify-content: space-between;
                }
            }
            &__button {
                margin-top: 50px;
            }
        }
        &-form {
            width: 376px;
            height: 556px;  
            row-gap: 32px;
            grid-column: span 4;
            background: #F7F6F6;
            border-radius: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            &__text {
                padding-top: 30px;
                font-weight: 600;
                font-size: 24px;
                line-height: 36px;
                color: #000000;
            }
            &__button {
                width: 289px;
                border: 1px solid #040404;
                border-radius: 20px;
                height: 37px;
                left: 121px;
                top: 983px;
                transition: all 2s;
                &:hover {
                    box-shadow: 0 0 10px #000000;
                }
                &-smal {
                    background: rgba(222, 215, 215, 0.41);
                    border: 1px solid #FFF;
                    box-sizing: border-box;
                    border-radius: 20px;
                    width: 30px;
                    height: 30px;
                    font-size: 15px;
                    line-height: 18px;
                    color: #000000;
                    &:hover {
                        background-color: #000000;
                        color: #FFF;
                    }
                }
            }
        }
    }   
    .form-box {
        width: 90%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        gap: 32px;
        align-content: flex-start;
        height: 143px;
    }  
    .form-input {
        background-color: #F7F6F6;
        border: none;
        border-bottom: 0.5px solid #000000;
        height: 31px;
        left: 837px;
        top: 523px;
    } 
    .cartBasket {
        display: flex;
        flex-direction: row;
        align-items: flex-start;
        margin-bottom: 10px;
        padding: 10px;
        border: 0.5px solid #CACDD8;
        border-radius: 15px;
        &-img {
            height: 33%;
            width: 33%;
        }
    }
</style>