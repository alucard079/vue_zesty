<template>
  <div class="background-yellow">
    <div class="d-flex justify-content-center text-center" v-if="content">
        <b-row>
            <b-col md="12" class="mt-5 mb-5">
                <div class="global-header">{{content.title}}</div>
            </b-col>
        </b-row>
    </div>
    <div class="d-flex justify-content-center" v-if="content">
        <b-card :img-src="content.hero_image" img-alt="Card image" :img-top="img_top" :img-left="img_left" class="mb-3 about-card-img-left">
            <b-card-text v-html="content.hero_content" class="about-card-headline text-left"></b-card-text>
            <b-card-text v-html="content.page_content" class="about-card-content text-left"></b-card-text>
        </b-card>
    </div>
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
        content: "",
        windowWidth: window.innerWidth,
        img_left: true,
        img_top: false,
      }
    },
    created() {
        this.onGetAbountContent();

        if (window.innerWidth <= 575.98 || window.innerWidth <= 768) {
          this.img_top = true;
          this.img_left = false;
        }
    },
    methods: {
      onGetAbountContent() {
        axios.get(`https://www.zesty.io/-/gql/about.json`)
        .then(response => {
            if(response.status === 200) {
                this.content = response.data[0];
            }
        })
        .catch(e => {
            console.log(e);
        })
      }
    }
  }
</script>