<template>
  <div class="background-yellow">
    <div class="d-flex justify-content-center text-center">
        <b-row>
            <b-col md="12" class="mt-5 mb-3">
                <div class="global-header">Home</div>
            </b-col>
        </b-row>
    </div>
    <b-row>
        <b-col md="12">
            <b-carousel
                id="carousel-1"
                v-model="slide"
                :interval="3000"
                controls
                indicators
                >
                <b-carousel-slide
                    v-for="(slide, index) in slides"
                    :key="index"
                >
                    <template #img>
                        <b-container class="d-flex justify-content-center py-5 px-2"> 
                            <b-card
                                :title="slide.title"
                                :sub-title="slide.subtitle"
                                :img-src="slide.image"
                                img-alt="Image"
                                img-top
                                tag="article"
                                style="max-width: 35rem;"
                                class="mb-2"
                            >
                                <div v-html="slide.content"></div>
                            </b-card>
                        </b-container>
                    </template>
                </b-carousel-slide>
            </b-carousel>
        </b-col>
    </b-row>
  </div>
</template>

<style lang="sass">
  @import '@/scss/app.scss';
</style>

<script>
import axios from 'axios';

  export default {
    data() {
      return {
        slide: 0,
        sliding: null,
        slides: [],
      }
    },
    created() {
        this.onGetSliderContent();
    },
    methods: {
      onSlideStart() {
        this.sliding = true
      },
      onSlideEnd() {
        this.sliding = false
      },
      onGetSliderContent() {
        axios.get(`https://www.zesty.io/-/gql/features.json`)
        .then(response => {
            if(response.status === 200) {
                this.slides = response.data;
                console.log(this.slides)
            }
        })
        .catch(e => {
            console.log(e);
        })
      }
    }
  }
</script>