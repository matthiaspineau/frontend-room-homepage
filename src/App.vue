<template>
  <div id="app" >
    <nav class="nav container">
      <div class="navbar" :class="{'active' : menuIsOpen}">
        <div class="btn__menu">
           <img v-if="!menuIsOpen" 
           :src="require('@/assets/images/icon-hamburger.svg')" alt="icon menu" 
           @click="openMenu()">
           <img v-if="menuIsOpen" 
           :src="require('@/assets/images/icon-close.svg')" alt="icon menu" 
           @click="closeMenu()">
        </div>
        <h1>
          <img :src="require('@/assets/images/logo.svg')" alt="logo room">
        </h1>
        <ul class="navbar__ul">
          <li class="navbar__li">home</li>
          <li class="navbar__li">shop</li>
          <li class="navbar__li">about</li>
          <li class="navbar__li">contact</li>
        </ul>
        <div class="divider" @click="closeMenu()"></div>
      </div>
    </nav>


    <div class="wrapper__article">
      <div class="container">
        <article-item  :item="items[index]"  @emit-go-prev="prev" @emit-go-next="next"></article-item>
      </div>
    </div>

    <footer class="container">
      <div class="bot">
        <div class="bot__left">
          <img :src="require('@/assets/images/image-about-dark.jpg')" alt="image salon">
        </div>
        <div class="bot__mid">
          <h3>About Our Fourniture</h3>
          <p> Our multifunctional collection blends design and function to suit your individual taste. Make each room unique, or pick a cohesive theme that best express your interests and what inspires you. Find the furniture pieces you need, from traditional to contemporary styles or anything in between. Product specialists are available to help you create your dream space.</p>
        </div>
        <div class="bot__right">
          <img :src="require('@/assets/images/image-about-light.jpg')" alt="image chaise">
        </div>
      </div>
    </footer>
  <!-- <div class="bot__right">
          <img :src="require('@/assets/images/mobile-image-hero-1.jpg')" alt="image chaise">
        </div> -->
  </div>
</template>

<script>
import ArticleItem from './components/ArticleItem.vue';

const items = [
  {
    id: 1,
    title: "Discover innovative ways to decorate",
    description: "We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.",
    imgMobile: "mobile-image-hero-1.jpg",
    imgDesktop: "desktop-image-hero-1.jpg"
  },
   {
    id: 2,
    title: "We are available all across the globe",
    description: "With stores all over the world, it's easy for you to find furniture for your home or place of business. Locally, we’re in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today.",
    imgMobile: "mobile-image-hero-2.jpg",
    imgDesktop: "desktop-image-hero-2.jpg"
  },
  {
    id: 3,
    title: "Manufactured with the best materials",
    description: "Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.",
    imgMobile: "mobile-image-hero-3.jpg",
    imgDesktop: "desktop-image-hero-3.jpg"
  }
]

export default {
  name: 'App',
  data() {
    return {
      menuIsOpen: false,
      items: items,
      index: 0
    }
  },
  methods: {
    openMenu() {
      console.log('open menu')
      this.menuIsOpen = true;
    },
    closeMenu() {
      console.log('open menu')
      this.menuIsOpen = false;
    },
    prev(payload) {
      if (payload.message == 1) {
        this.index = 2
      } else {
        this.index = (payload.message - 1) - 1
      }
    },
    next(payload) {
      if (payload.message == 3) {
        this.index = 0
      } else {
        this.index = (payload.message - 1) + 1
      }
    }
  },
  components: {
    ArticleItem,
  }
}
</script>

<style src="@/assets/scss/app.scss" lang="scss"></style>
