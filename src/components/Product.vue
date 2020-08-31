<template>
  <div class="product">
    <div :class="'product-inner ' + product.color">
      <div class="product-text-wrap">
      </div>
      <div class="product-image-wrap">
        <img :src="product.imgsrc" class="image" />
      </div>
      <div class="product-detail">
        <h2>{{ product.title }}</h2>
        <p>{{product.artist}}</p>
        <p>{{product.time}}</p>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'product',
  props: ['product']
}
</script>

<style>
    .product {
    /*flex: 1 1 33.333%;*/
    width: 100%;
    padding: 25px;
    border-radius: 25px;
  }
  .product-inner {
    position: relative;
    padding: 25px;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
    perspective: 1000px;
  }
  .product-inner.green {
    background-image: linear-gradient(to bottom right, #24D484, #116432);
  }
  .product-inner.blue {
    background-image: linear-gradient(to bottom left, #24D484, #2474C4 70%);
  }
  .product-inner.pink {
    background-image: linear-gradient(to bottom right, #F444A4, #1168D4);
  }
  .product-text-wrap {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 0;
    overflow: hidden;
    perspective: 1000px;
  }
  
  .product-text-wrap h2 {
    color: #131313;
    font-size: 128px;
    font-weight: 900;
    opacity: 0.2;
    transform-origin: center;
  }
  .product-image-wrap {
    position: relative;
    z-index: 1;
    transform-origin: center;
  }
  .product-image-wrap .image {
    width: 100%;
    filter: drop-shadow(0px 0px 12px rgba(0, 0, 0, 0.25));
  }
  .product-detail {
    background-color: #f3f3f3;
    padding: 25px;
    margin: 0px -25px -25px;
  }
  .product-detail h2 {
    font-size: 24px;
    font-weight: 700;
    color: #292929;
    margin-bottom: 5px;
  }
  .product-detail p {
    font-size: 14px;
    font-weight: 300;
    margin-bottom: 5px;
    color: #282828;
  }
</style>