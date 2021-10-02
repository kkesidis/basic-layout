<template>
  <div id="app">
    <header class="header">
      <div class="header__menu" @click="menuToggle = !menuToggle">
        <Menu />
      </div>
      <div class="header__logo">
        <Logo />
      </div>
    </header>
    <div class="main">
      <nav class="nav" :class="{'nav__open': menuToggle}">
        <ul class="nav__items">
          <li class="nav__item" v-for="i in 5" :key="`page-${i}`">Page {{i}}</li>
        </ul>
        <div class="nav__divider"/>
        <ul class="nav__items">
          <li class="nav__item" v-for="i in 100" :key="`widget-${i}`">Widget {{i}}</li>
        </ul>
      </nav>
      <main class="content">
        <HelloWorld />
      </main>
    </div>
  </div>
</template>

<script>
import Logo from './components/icons/Logo.vue';
import Menu from './components/icons/Menu.vue';
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    Logo,
    Menu,
    HelloWorld,
  },
  data: () => ({
    menuToggle: false
  }),
}
</script>

<style lang="scss">
$medium-and-up: 'only screen and (min-width: 768px)';
$nav-width: 250px;

body {
  margin: 0;
  padding: 0;
}

#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  font-family: Roboto;

  .header {
    display: flex;
    align-items: center;
    background-color: #93C5FD;
    border-bottom: 2px solid #60A5FA;
    padding: 0.5rem 1rem;

    &__menu {
      cursor: pointer;
      margin-right: 1rem;
      @media #{$medium-and-up} {
        display: none;
      }
    }
  }

  .main {
    flex: 1;
    display: flex;
    position: relative;
    overflow: auto;

    .nav {
      height: 100%;
      padding: 0.5rem;
      width: $nav-width;
      background-color: #E5E7EB;
      box-sizing: border-box;
      transition: 0.3s;
      overflow: auto;

      /** mobile behavior */
      position: absolute;
      transform: translateX(-#{$nav-width});

      /** mobile [open] behavior */
      &__open {
        transform: translateX(0);
      }

      /** medium and up behavior */
      @media #{$medium-and-up} {
        position: static;
        transform: translateX(0);
      }

      &__items {
        list-style-type: none;
        padding: 0;
        margin: 0;
      }

      &__item {
        cursor: pointer;
        padding: 0.5rem 1rem;
        border-radius: 5px;
        transition: 0.1s ease-in-out;
        &:hover {
          background-color: #93C5FD;
        }
      }

      &__divider {
        border-bottom: 1px solid #93C5FD;
        margin-top: 0.5rem;
        margin-bottom: 0.5rem;
      }
    }

    .content {
      flex: 1;
      overflow: auto;
      padding: 0.5rem;
    }
  }
}
</style>
