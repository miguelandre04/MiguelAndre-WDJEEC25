  <template>
    <div class="home">
      <div class="outside">
        <p>Reponse to question 1: 5</p>
        <p>25/04/2024</p>
      </div>
      <Carousel class ="carousel" v-slot="{currentSlide}">
        <Slide>
          <div class="slide1" v-show="currentSlide == 1">
            <p>How many departments does JEEC have?</p>
          </div>
        </Slide>
        <Slide>
          <div class="slide2" v-show="currentSlide == 2">
            <p>25/04/2024</p>
          </div>
        </Slide>
        <Slide>
          <div class="flexbox" v-show="currentSlide == 3">
            <img :src="require(`../assets/challenge2.png`)" alt="">
            <p>Come learn with us!</p>
          </div>
        </Slide>
        <Slide>
          <div class="slide4" v-show="currentSlide == 4">
            <img :src="require(`../assets/challenge.png`)" alt="">
          </div>
        </Slide>
      </Carousel>
    </div>
  </template>
  
  <script>
  import Carousel from "../components/CarouselWrapper.vue";
  import Slide from "../components/SlideItem.vue";
  
  export default {
    name: 'App',
    components: {
      Carousel,
      Slide
    },
  }
  </script>

<style lang="scss" scoped>

.carousel {
  position: relative;
  width: 75%;
  height: 75vh;

  .slide-info {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .slide4 img {
  width: 50%;
  position: absolute;
  top: 50%;
  left: 50%; 
  transform: translate(-50%, -50%);
}


  .slide1, .slide2 {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 70px;
  }
  .slide1 {
    left: 57%;
  }


  .flexbox {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  text-align: center;
}

.flexbox img {
  width: 50%;
  margin-bottom: 20px;
}

.flexbox p {
  font-size: 20px; 
}
}

.outside {
  font-size: 20px; 
  margin-left: 1100px;
}

</style>
