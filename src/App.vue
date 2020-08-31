
<template>
  <main id="app" @mousemove="mousemove">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <div class='head'>
      <img src="./assets/logo.svg" id='logo'>
      <h1 id='title'>Baja Music</h1>
    </div><hr>

    <section class="player">
        <h2 class="song-title">{{ current.title }} - <span>{{ current.artist }}</span></h2>
        <div class="controls">
          <button class="prev" @click="prev"><i class="fa fa-backward"></i></button>
          <button class="play" v-if="!isPlaying" @click="play"><i class="fa fa-play"></i></button>
          <button class="pause" v-else @click="pause"><i class="fa fa-pause"></i></button>
          <button class="next" @click="next"><i class="fa fa-forward"></i></button>
        </div>
    </section>
    
    <section class="products" @click="play">
      <Product
        v-for="product in products"
        :key="product.color"
        :product="product"
      />
    </section>
  </main>
</template>


<script>

import Product from './components/Product';
export default {
  name: 'app',
  components: {
    Product
  },
  data () {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      products: [
        {
          title: 'Song 1',
          color: 'pink',
          bgtext: 'NIKE',
          imgsrc: require('./assets/blue-shoe.png'),
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          time:'5:00'
        },
        {
          title: 'Song 2',
          color: 'pink',
          bgtext: 'AIR',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/blue-shoe.png'),
          time:'5:00'
        },
        {
          title: 'Song 3',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/blue-shoe.png'),
          time:'5:00'
        },
        {
          title: 'Song 4',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },
        {
          title: 'Song 5',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },
        {
          title: 'Song 6',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },
        {
          title: 'Song 7',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 8',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 9',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 10',
          color: 'pink',
          bgtext: 'MAX',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          artist:'Someone good singer',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 11',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 12',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 13',
          color: 'pink',
          bgtext: 'MAX',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          artist:'Someone good singer',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 14',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 15',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png'),
          time:'5:00'
        },{
          title: 'Song 16',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png')
        },{
          title: 'Song 17',
          color: 'pink',
          bgtext: 'MAX',
          artist:'Someone good singer',
          src:'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-8.mp3',
          imgsrc: require('./assets/pink-shoe.png')
        },
      ],
      player:new Audio()
    }
  },
  methods: {
        play (product) {
      if (typeof product.src != "undefined") {
        this.current = product;
        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener('ended', function () {
        this.index++;
        if (this.index > this.products.length - 1) {
          this.index = 0;
        }
        this.current = this.products[this.index];
        this.play(this.current);
      }.bind(this));
      this.isPlaying = true;
    },
    pause () {
      this.player.pause();
      this.isPlaying = false;
    },
    next () {
      this.index++;
      if (this.index > this.products.length - 1) {
        this.index = 0;
      }
      this.current = this.products[this.index];
      this.play(this.current);
    },
    prev () {
      this.index--;
      if (this.index < 0) {
        this.index = this.products.length - 1;
      }
      this.current = this.products[this.index];
      this.play(this.current);
    }
  },
  created () {
    this.current = this.products[this.index];
    this.player.src = this.current.src;
  }
}


  
</script>

    
    

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body {
    font-family: 'Raleway', sans-serif;
  }
  main {
    width: 100vw;
    min-height: 100vh;
    
    background-color:#f8f8f8;
    /*display: flex;*/
    /* justify-content: center;
    align-items: center; */
  }
  .products {
    display: grid;
    grid-template-columns: repeat(5,1fr);
    max-width: 1280px;
    padding: 25px;
    margin: 0 auto;
    border-radius: 25px;
  }
  .prev,.play,.pause,.next{
    background-image: linear-gradient(to bottom right, #F444A4, #1168D4);
    margin:5px;
    padding:10px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
  }
  .fa{
    color:white;  
  }
  .player{
    margin: 40px 100px;
    background: #fafafa;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
    padding: 25px;
    border-radius: 25px;
    align-content: center;
    align-items: center;
    justify-items: center;
  }

  #logo{
    width: 15%;
    padding: 15px;
    margin: 10px;
    
  }

  .head{
   display: flex;
   flex-direction: row;
  }
  #title{
    vertical-align: -webkit-baseline-middle;
    text-transform: uppercase;
    font-weight: 750;
    font-size: 80px;
    align-items: center;
    padding-top: 3%;
  }
  hr{
    opacity:0.5;
    width: 80%;
    margin-left: 10%;
  }
</style>