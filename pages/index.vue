<template>
  <div>
     <v-ons-page>
        <v-ons-toolbar>
          <div class="left"><ons-toolbar-button @click="carouselIndex > 0 && carouselIndex--">i--</ons-toolbar-button></div>
          <div class="center">Index: {{carouselIndex}}</div>
          <div class="right"><ons-toolbar-button @click="carouselIndex < 2 && carouselIndex++">i++</ons-toolbar-button></div>
        </v-ons-toolbar>

        <v-ons-carousel fullscreen swipeable auto-scroll overscrollable
          :index.sync="carouselIndex"
        >
          <v-ons-carousel-item v-for="(value, key) in items" :style="{backgroundColor: value}" :key="key">
            <div style="text-align: center; font-size: 30px; margin-top: 20px; color: #fff;">{{key}}</div>
          </v-ons-carousel-item>
        </v-ons-carousel>

        <div :style="dots">
          <span :index="dotIndex - 1" v-for="dotIndex in Object.keys(items).length" :key="dotIndex" style="cursor: pointer" @click="carouselIndex = dotIndex - 1">
            {{ carouselIndex === dotIndex - 1 ? '\u25CF' : '\u25CB' }}
          </span>
        </div>
      </v-ons-page>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carouselIndex: 0,
      items: {
        BLUE: '#085078',
        DARK: '#373B44',
        ORANGE: '#D38312'
      },
      dots: {
        textAlign: 'center',
        fontSize: '30px',
        color: '#fff',
        position: 'absolute',
        bottom: '40px',
        left: 0,
        right: 0
      }
    };
  }
};
</script>
