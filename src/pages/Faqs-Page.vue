<template>
    <div class="background-yellow">
        <b-container>
            <div class="d-flex justify-content-center text-center">
                <b-row>
                    <b-col md="12" class="mt-5 mb-5">
                        <div class="global-header">Frequently Asked Questions</div>
                    </b-col>
                </b-row>
            </div>
            <div class="accordion" role="tablist">
                <b-card no-body class="mb-4" v-for="(section, index) in sections" :key="index">
                    <b-card-header header-tag="header" class="p-1" role="tab">
                        <b-button block v-b-toggle="`accordion-${index}`" class="global-btn-yellow">
                            {{`${section.title}?`}}
                        </b-button>
                    </b-card-header>
                    <b-collapse :id="`accordion-${index}`" visible accordion="my-accordion" role="tabpanel">
                        <b-card-body>
                            <b-card-text v-html="section.text_content"></b-card-text>
                        </b-card-body>
                    </b-collapse>
                </b-card>
            </div>
        </b-container>
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
        sections: [],
        text: `
          Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry
          richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor
          brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon
          tempor, sunt aliqua put a bird on it squid single-origin coffee nulla
          assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore
          wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher
          vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic
          synth nesciunt you probably haven't heard of them accusamus labore VHS.
        `
      }
    },
    created() {
        this.onGetSections();
    },
    methods: {
      onGetSections() {
        axios.get(`https://www.zesty.io/-/gql/platform_section.json`)
        .then(response => {
            if(response.status === 200) {
                this.sections = response.data.filter((section,index) => index <= 4);
            }
        })
        .catch(e => {
            console.log(e);
        })
      }
    }
  }
</script>