<template>
    <div class="carousel">
        <slot :currentSlide="currentSlide" />

        <div class="navigate">
            <div class="toggle-page left">
                <i @click="prevSlide" class="fas fa-chevron-left"></i>
            </div>
            <div class="toggle-page right">
                <i @click="nextSlide" class="fas fa-chevron-right"></i>
            </div>
        </div>
        <div class="pagination">
            <span @click="goToSlide(index)" v-for="(slide,index) in getSlideCount" :key="index" :class="{active : index + 1 === currentSlide}">
            </span>
        </div>

    </div>  
</template>

<script>
import {ref, onMounted} from "vue";
export default {
    setup() {
        const currentSlide = ref(1);
        const getSlideCount = ref(null);
        const autoPlayEnabled = ref(true);
        const timeoutDuration = ref(5000);
        let intervalId;

        const nextSlide = () => {
            if (currentSlide.value === getSlideCount.value){
                currentSlide.value = 1;
            } else {
                currentSlide.value += 1;
            }
            restartAutoplay();
        };

        const prevSlide = () => {
            if (currentSlide.value === 1){
                currentSlide.value = getSlideCount.value;
            } else {
                currentSlide.value -= 1;
            }
            restartAutoplay();
        };

        const goToSlide = (index) => {
            currentSlide.value = index + 1;
            restartAutoplay();
        };

        const autoplay = () => {
            intervalId = setInterval(() => {
                nextSlide()
            }, timeoutDuration.value)
        };

        const restartAutoplay = () => {
            clearInterval(intervalId);
            if (autoPlayEnabled.value) {
                autoplay();
            }
        };

        onMounted(() => {
            getSlideCount.value = document.querySelectorAll('.slide').length;
            if (autoPlayEnabled.value) {
                autoplay();
            }
        })

        return {currentSlide, nextSlide, prevSlide, getSlideCount, goToSlide};
    },
}
</script>


<style lang="scss">
.carousel {
  position: relative;
}

.navigate {
  padding: 0 16px;
  height: 100%;
  width: 100%;

  .right {
    margin-left: 75px;
    }

  .toggle-page {
    position: absolute;
  top: 82%;
  left: 45%; 
    }

    i {
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    background-color: rgb(47, 116, 201);
    color: #fff;
    }
}

.pagination {
    position: absolute;
    bottom: 24px;
    width: 100%;
    display: flex;
    gap: 16px;
    justify-content: center;
    align-items: center;

    span {
        cursor: pointer;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background-color: #fff;
        box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
    }

    .active {
        background-color: rgb(47, 116, 201);
    }
}

</style>
