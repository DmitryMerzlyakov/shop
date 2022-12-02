<template>
  <div class="shop">
    <div class="main" id="mainTop">
      <header class="main__header">
              <a class="logo" href="index.html"><img class="logo__link" src="../assets/image/logo.svg" alt="myLogo"></a>
              <input placeholder="Поиск" class="main__header-input" type="text">
              <nav class="main__header-nav">
                  <a class="main__header-nav-page" href="#">Регистация</a>
                  <a class="main__header-nav-page" href="#">Вход</a>
              </nav>
      </header>
      <section class="main__content">
              <h1 class="main__content-h1">Всё, чего заслуживает ваш дом</h1>
              <p class="main__content-description">Наша мебель — ваше отражение</p>
              <a class="main__content-link" href="#catalogTop">Перейти в каталог</a>
      </section>
    </div>
    <vCatalog />
    <footer class="footer">
        <a href="index.html" class="footer__logo">
            <img src="../assets/image/int.svg" alt="myLogo">
        </a>
        <nav class="footer__menu">
            <h4 class="footer__h4">Меню</h4>
            <a class="footer__link" href="#mainTop">Главная</a>
            <a class="footer__link" href="#catalogTop">Каталог</a>
            <a class="footer__link" href="#bascetTop">Корзина</a>
        </nav> 
        <div class="footer__contact">  
            <h4 class="footer__h4">Контакты</h4>
            <a class="footer__link" href="tel:++7 908 800 80 80">+7 908 800 80 80</a><br>
            <a class="footer__link" href="mailto:help@interier.com">help@interier.com</a><br>
            <div class="social-media">
                <a href="#"><img src="../assets/image/facebook.svg" alt="facebook"></a>
                <a href="#"><img src="../assets/image/inst.svg" alt="inst"></a>
                <a href="#"><img src="../assets/image/twitter.svg" alt="twitter"></a> 
            </div>
        </div>
        <div class="footer__subscription">    
            <form class="subscription" action="#">
                <p class="subscription__news">Получайте наши новости и обновления</p>
                <input placeholder="Email Address" class="subscription__email" type="email">
                <button class="subscription__button">Подписаться</button>
            </form>
        </div>
    </footer> 
  </div>  
</template>
  
<script>
import vCatalog from '../components/catalog.vue';

export default {
  name: 'vMain',
  components: {
    vCatalog
  },
  data() {
    return {}
  }
}
</script>
  
<style lang="scss">
  .main {
    background-image: url(../assets/image/topback.jpg);
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    height: 735px;
    &__header {
        padding: 16px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 0.5px solid rgba(255, 255, 255, 0.8);
        &-input {
            width: 288px;
            height: 41px;
            box-sizing: border-box;
            left: 39.17%;
            right: 36.83%;
            top: 23.03%;
            bottom: 23.03%;
            border: 1px solid #FFF;
            border-radius: 20px;
            background-color: transparent;
            outline: none;
            font-style: normal;
            font-weight: 400;
            font-size: 16px;
            line-height: 20px;
            color: #FFF;
            padding-left: 32px;
            padding-right: 32px;
            transition: background-color 3s;
            &::placeholder {
                color: #FFF;
            }
            &:hover {
                background-color: #888888;
                color: #000000;
            }
        }
        &-nav {
        display: flex;
        padding: 0px;
        gap: 32px;
        width: 170px;
        height: 20px;
        flex: none;
        order: 2;
        flex-grow: 0;
            &-page {
            font-size: 16px;
            line-height: 20px;
            color: #FFF;
            transition: background-color 1s;
            &:hover {
                color: #C4C4C4;
            }
            }
        }
    }
    &__content {
        &-h1 {
        font-weight: 500;
        font-size: 64px;
        line-height: 70px;
        margin: 150px 0 0 32px;
        font-style: normal;
        color: #FFF;
        }
        &-link {
            font-size: 16px;
            line-height: 24px;
            font-style: normal;
            font-weight: 400;
            text-decoration-line: underline;
            color: #FFF;
            margin-left: 35px;
            &:hover {
                color: #888888;
            }
        }
        &-description {  
            font-weight: 400;
            font-size: 25px;
            line-height: 17px;
            color: #FFF;
            margin-left: 35px;
        }
    }
  }
  .footer {
    margin-top: 64px;
    height: 207px;
    left: 0px;
    top: 3383px;
    padding-top: 32px;
    background: #F7F6F6;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: center;
    justify-content:  space-evenly;
    align-items: flex-start;
    &__logo {
        font-weight: 600;
        font-size: 36px;
        line-height: 44px;
        color: #000000;
    }
    &__menu {
        display: flex;
        flex-wrap: wrap;
        flex-direction: column;
        align-content: space-around;
        justify-content: center;
        align-items: center;
        grid-gap: 12px;
    }
    &__h4 {
        font-weight: 500;
        font-size: 24px;
        line-height: 29px;
        color: #000000;
        margin-top: 0;
        margin-bottom: 12px;
    }
    &__contact {
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        align-content: flex-start;
        align-items: center;
        justify-content: center;
    }
    &__link {
        font-weight: 500;
        font-size: 14px;
        line-height: 17px;
        color: #888888;
        text-decoration: none;
        &:hover {
            color: #000000;
        }
    }
  }
  .subscription {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    align-content: space-around;
    justify-content: center;
    align-items: center;
        &__news {
        font-weight: 400;
        font-size: 14px;
        line-height: 16px;
        color: #000000;
        margin-bottom: 16px;
        margin-top: 0;
          }
        &__email {
            width: 275px;
            height: 46px;
            background: #FFF;
            border: 1px solid #C4C4C4;
            box-sizing: border-box;
            border-radius: 20px;
            color: #C4C4C4;
            padding-top: 16px;
            margin-bottom: 12px;
            background-color: #FFF;
            outline: none;
            font-style: normal;
            font-weight: 400;
            font-size: 16px;
            line-height: 20px;
            color: #000000;
            padding: 15px 105px 14px 25px;
            transition: background 3s;
            &:hover {
                background-color: #888888;
            }
            &:active {
                background-color: #888888;
            }
        }
        &__button {
            background: rgba(222, 215, 215, 0.41);
            border: 1px solid #FFF;
            box-sizing: border-box;
            border-radius: 20px;
            width: 275px;
            height: 46px;
            font-size: 15px;
            line-height: 18px;
            color: #000000;
            &:hover {
                background-color: #000000;
                color: #FFF;
            }
        }
  }
  .social-media {
    display: flex;
    align-items: center;
  }
</style>