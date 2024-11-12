<template>
  <header>
    <div class="header-container">
      <nav class="mobile-nav">
        <nuxt-link to="#profile" class="icon"><img :src="profileIcon"/></nuxt-link>
        <nuxt-link to="#search" class="icon"><img :src="searchIcon"/></nuxt-link>
      </nav>
      <nuxt-link to="/" class="logo"><img :src="logoIcon"/></nuxt-link>
      <nav class="desktop-nav">
        <nuxt-link to="#search" class="icon"><img :src="searchIcon"/></nuxt-link>
        <nuxt-link to="#fav" class="icon"><img :src="favIcon"/></nuxt-link>
        <nuxt-link to="#profile" class="icon"><img :src="profileIcon"/></nuxt-link>
        <nuxt-link to="#cart" class="icon"><img :src="cartIcon"/></nuxt-link>
      </nav>
      <nav class="mobile-nav">
        <nuxt-link to="#cart" class="icon"><img :src="cartIcon"/></nuxt-link>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
        logoIcon: require('~/assets/icons/logo.svg'),
        searchIcon: require('~/assets/icons/search.svg'),
        favIcon: require('~/assets/icons/fav.svg'),
        profileIcon: require('~/assets/icons/profile.svg'),
        cartIcon: require('~/assets/icons/cart.svg'),
    }
  }
}
</script>

<style scoped>
.header-container {
  display: flex;
  justify-content: end;
  align-items: center;
  padding: 30px 48px;
  position: relative;
}

.logo {
    position: absolute;
    top: calc(50% - 12px);
    left: calc(50% + 26px);
}

nav .icon {
    width: 20px;
    height: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

nav {
    display: flex;
    flex-direction: row;
    align-items: start;
    gap: 16px;
}

.mobile-nav {
    display: none
}

@media (max-width: 645px) {
    .mobile-nav {
        display: flex;
    }

    .desktop-nav {
        display: none;
    }

    .header-container {
        justify-content: space-between;
        padding: 16px 20px;
    }

    .logo {
        position: static;
    }
}
</style>