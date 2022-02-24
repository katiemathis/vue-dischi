<template>
    <div class="container main_container">
        <div v-if="loadingInProgress">
            <PageLoading />
        </div>
        
        <div class="row row-cols-lg-6 row-cols-md-4 row-cols-3 justify-content-center" v-else>
                <SongCard 
                    v-for= "(cardItem, index) in cardItems" :key= "index"
                     :myTile= "cardItem" 
                />
        </div>
    </div>
</template>

<script>

const axios = require('axios');

import SongCard from './partials/SongCard.vue';
import PageLoading from '../components/partials/PageLoading.vue'

export default {
    name: 'MainContent',
    components: {SongCard, PageLoading},
    data () {
          return {
              cardItems: [],
              loadingInProgress: true,
          }      
    },
    methods: {
            getSongs() {
                // Make a request for a user with a given ID
                axios.get('https://flynn.boolean.careers/exercises/api/array/music')
                .then((response) => {
                    this.cardItems = response.data.response;
                    this.loadingInProgress = false;
                    
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
            }
        },
        mounted() {
            document.onreadystatechanges = () => {
                if (document.readyState == "complete") {
                    this.isloaded = true;
                }
            }
        },
        created() {
            this.getSongs();
            this.isLoaded = true;
            
        }
}

</script>

<style scoped lang="scss">

@import '../style/general.scss';

* {
    background-color: #17212d;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    color: white;
}






</style>