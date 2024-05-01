<template>
  <div class="home">
    <div class="outside">
      <p>Reponse to question 1: 5</p>
      <p>Selected Date outside Carousel: {{ selectedDate }}</p>
    </div>
    <Carousel class ="carousel" v-slot="{currentSlide}">
      <Slide>
        <div class="slide1" v-show="currentSlide == 1">
          <p>How many departments does JEEC have?</p>
        </div>
      </Slide>
      <Slide>
        <div v-show="currentSlide === 2">
          <datepicker v-model="selectedDate" @date-selected="updateSelectedDate" />
          <p>Selected Date: {{ selectedDate }}</p>
        </div>
      </Slide>
      <Slide>
        <div class="flexbox" v-show="currentSlide == 3">
          <p class="tittle">Interrogation of wind Farms into</p>
          <p class="2titulo">Eletricity Grids</p>
          <p class="2titulo">Workshop</p>
          <p class="mais">by Vestas</p>
          <p class="menos">This workshop</p>
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
  import Datepicker from "vue3-datepicker";
  
  export default {
    name: 'App',
    components: {
      Carousel,
      Slide,
      Datepicker,
    },

    data() {
    return {
      selectedDate: null,
    };
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


  .flexbox p {
  display: flex;
  flex-direction: column;
  justify-content:space-evenly;
  height: 100%;
  padding: 10px;
  background-color: rgb(132, 176, 229);
  margin: 0;
}

.tittle {
  font-size: 30px; 
  margin: auto;
}

.mais {
  font-size: 30px; 
}

.menos {
  font-size: 15px;
}
}

.outside {
  font-size: 20px; 
  margin-left: 1100px;
}

</style>
