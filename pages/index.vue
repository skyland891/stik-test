<template>
  <main>
    <section class="product">
      <div class="product-gallery">
        <div class="product-thumbnails">
          <img :src="min_1" alt="Миниатюра 1">
          <img :src="min_2" alt="Миниатюра 2">
          <img :src="min_3" alt="Миниатюра 3">
        </div>
        <img :src="main" alt="Жакет удлиненный белый" class="product-main-image">
      </div>

      <article class="product-info">
        <h1>Жакет удлиненный, белый</h1>
        <p class="main-price">8500 RUB</p>
        <form class="product-options">
            <fieldset class="size-selector">
                <legend class="size-label">Размер</legend>
                <div class="size-options">
                  <button
                    v-for="(size) in allSizes"
                    :key="size"
                    :class="{ 'size-option': true, active: selectedSize === size, 'not-availabel': !getIsAvailabelSize(size) }"
                    @click.prevent="selectSize(size)"
                    type="button"
                    :aria-pressed="selectedSize === size"
                  >
                    {{ size }}
                  </button>
                </div>
            </fieldset>

          <fieldset class="color-selector">
            <legend class="color-legend">Цвет</legend>
            <label class="color-label">
              <input hidden type="radio" name="color" value="white" checked>
              <span class="color-swatch white" style="background-color: #FFFFFF;"></span>
            </label>
            <label class="color-label">
              <input hidden type="radio" name="color" value="black">
              <span class="color-swatch" style="background-color: #000000;"></span>
            </label>
            <label class="color-label">
              <input hidden type="radio" name="color" value="beige">
              <span class="color-swatch" style="background-color: #F9F1DC;"></span>
            </label>
          </fieldset>

          <div class="button-group">
            <button type="submit" class="add-to-cart">Добавить в корзину</button>
            <button class="add-to-fav">
              <img :src="addToFavIcon" alt="Добавить в избранное"/>
            </button>
          </div>
        </form>

        <details class="product-details">
          <summary>
            <span>Описание</span>
            <span>+</span>
        </summary>
          <p>Описание товара...</p>
        </details>
        <details class="product-details">
          <summary>
            <span>Состав и уход</span>
            <span>+</span>
        </summary>
          <p>Состав и уход...</p>
        </details>
      </article>
    </section>

    <section class="related-products">
      <h2>Похожие товары</h2>
      <ul class="product-list">
        <li class="product-card">
          <img :src="same_1" alt="Товар 1">
          <p>платье с рукавами, белый</p>
          <p class="price">12 500 RUB</p>
        </li>
        <li class="product-card">
          <img :src="same_2" alt="Товар 2">
          <p>жакет двойной, серо-голубой</p>
          <p class="price">8500 RUB</p>
        </li>
        <li class="product-card">
          <img :src="same_3" alt="Товар 3">
          <p>платье макси с ярусами, белый</p>
          <p class="price">12 500 RUB</p>
        </li>
        <li class="product-card">
          <img :src="same_4" alt="Товар 4">
          <p>комбинезон со стойкой, чёрный</p>
          <p class="price">8500 RUB</p>
        </li>
      </ul>
    </section>
  </main>
</template>

<style scoped>

.size-selector {
  display: flex;
  flex-direction: column;
  margin-top: 30px;
  border: none;
  padding: 0;
}

.size-label {
  margin-bottom: 8px;
}

.size-options {
  display: flex;
  gap: 8px;
}

.size-option {
  width: 65px;
  height: 30px;
  font-size: 10px;
  color: #333333;
  background-color: white;
  border: 1px solid #333333;
  cursor: pointer;
}

.size-option:hover {
  background-color: #e0e0e0;
}

.size-option.active {
  background-color: #333333;
  color: #fff;
  border-color: #333333;
}

.size-option.not-availabel {
    pointer-events: none;
    color: #BDBDBD;
    border-color: #BDBDBD;
}

.product {
  display: flex;
  flex-wrap: wrap;
  gap: 60px;
  justify-content: center;
}

.product-gallery {
  display: flex;
  gap: 30px;
  min-width: 300px;
  padding: 0 12px 0;
}

.product-main-image {
  width: 100%;
  max-width: 500px;
}

.product-thumbnails {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.product-thumbnails img {
  width: 70px;
  height: 87px;
  cursor: pointer;
}

.product-info {
  max-width: 360px;
  width: 360px;
  position: relative;
}

.product-info h1 {
    font-family: Helvetica;
    font-size: 12px;
    font-weight: 400;
    line-height: 16px;
    text-transform: uppercase;
    margin-bottom: 8px;
}

.price {
  font-family: Helvetica;
  font-size: 12px;
  font-weight: 400;
  line-height: 14px;
  font-size: 10px;
  color: #333333;
  margin: 10px 0;
}

.product-options fieldset {
  border: none;
}

.button-group {
    display: flex;
    flex-direction: row;
    max-height: 44px;
    gap: 10px;
    margin-bottom: 40px;
}

.add-to-cart {
  display: block;
  padding: 10px;
  background-color: #000;
  flex-grow: 1;
  color: #fff;
  text-align: center;
  border: none;
  cursor: pointer;
}

.add-to-fav {
    display: block;
    border: 1px solid black;
    padding: 13.5px 15.5px;
    background-color: transparent;
    cursor: pointer;
}

.color-swatch {
  display: inline-block;
  width: 28px;
  height: 28px;
  margin-right: 10px;
  cursor: pointer;
  position: relative;
}

.color-swatch.white {
    border: 1px solid #BDBDBD;
}

.color-label input[type="radio"]:checked + .color-swatch::after{
    content: '';
    width: 34px;
    height: 1px;
    background-color: #4F4F4F;
    position: absolute;
    bottom: -4px;
    left: -3px;
}

.related-products {
  padding: 40px;
}

.related-products h2 {
  font-size: 20px;
  margin-bottom: 20px;
}

.product-list {
  display: grid;
  grid-gap: 8px;
  grid-template-columns: repeat(4, 1fr);
}

.product-card {
  margin: 10px;
  text-align: start;
}

.product-card img {
  width: 100%;
  height: auto;
  border: 1px solid #ddd;
}

.color-legend {
    margin-bottom: 6px;
}

.product-details {
    position: relative;
    padding: 13px 0;
}

.product-details summary {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.product-details summary span {
    font-family: Helvetica;
    font-size: 10px;
    font-weight: 400;
    line-height: 14px;
    color: #333333;
    text-transform: uppercase;
}

.product-details summary:last-of-type span {
    font-family: Helvetica;
    font-weight: 400;
    line-height: 14px;
    color: #333333;
    font-size: 12px;
    cursor: pointer;
}

.product-details:first-of-type::before {
    position: absolute;
    content: '';
    height: 1px;
    background: #E0E0E0;
    top: 0;
    width: 100%;
}

.product-details::after {
    position: absolute;
    content: '';
    height: 1px;
    background: #E0E0E0;
    bottom: 0;
    width: 100%;
}

.color-selector {
    margin: 35px 0;
}

@media (max-width: 375px) {
  .product {
    flex-direction: column;
  }

  .product-gallery {
    padding: 0;
  }

  .product-info {
    padding: 0 16px;
  }

  .product-thumbnails {
    display: none;
  }

  .add-to-cart {
    display: none;
  }

  .add-to-fav {
    position: absolute;
    border: none;
    top: -13px;
    right: 0;
  }

  .product-list {
    grid-template-columns: repeat(2, 1fr);
  }

  .related-products {
    padding: 40px 16px 0;
  }

  .button-group {
    margin: 0;
  }

  .main-price {
    font-family: Helvetica;
    font-size: 12px;
    font-weight: 400;
    line-height: 16px;
  }
}

@media (min-width: 376px) and (max-width: 645px) {
    .product-gallery {
        flex-direction: column;
        gap: 15px;
    }

    .product-thumbnails {
        flex-direction: row;
    }
}
</style>

<script>
export default {
  data() {
    return {
      main: require('~/assets/images/main.png'),
      min_1: require('~/assets/images/min-1.png'),
      min_2: require('~/assets/images/min-2.png'),
      min_3: require('~/assets/images/min-3.png'),
      same_1: require('~/assets/images/same-1.png'),
      same_2: require('~/assets/images/same-2.png'),
      same_3: require('~/assets/images/same-3.png'),
      same_4: require('~/assets/images/same-4.png'),
      addToFavIcon: require('~/assets/icons/add-to-fav.svg'),
      allSizes: ['XS', 'S', 'M'],
      notAvailabelSizes: ['M'],
      selectedSize: null,
    }
  },
  methods: {
    selectSize(size) {
      this.selectedSize = size;
    },
    getIsAvailabelSize(size) {
        return !this.notAvailabelSizes.includes(size);
    }
  },
}
</script>