<template>
  <div class="header_container d-flex justify-content-between">
      <div class="row header col-1 ">
          <img src="../assets/logo-small.svg" alt="">
      </div>
      <div class="dead_space row header col-6">
      </div>
      <div class="row header col-2">
            <select class="debug m-4 select_genre">
                <option value="">Genre</option>
                <option v-for="(genreItem, index) in genreItems" 
                :key="index"
                :value= "genreItem.genre" >{{genreItem.genre}}
                </option>

          </select>
        
      </div>
            <div class="dead_space row header col-1">
      </div>



  </div>
</template>

<script>
const axios = require('axios');

//import MySelectors from './partials/MySelectors.vue'

export default {
    name: 'MyHeader',
            data () {
            return {
                genreItems: [],
                loadingInProgress: true,
            }
        },
        computed: {
            uniqueQuestions() {
                return this.genreItems.reduce((seed, current) => {
                    return Object.assign(seed, {
                    [current.genre]: current
                    });
                });
            },
        },


       methods: {
            getGenres() {
                // Make a request for a user with a given ID
                axios.get('https://flynn.boolean.careers/exercises/api/array/music')
                .then((response) => {
                    this.genreItems = response.data.response;
                    this.loadingInProgress = false;
                    
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
            }
        },
        mounted() {
            /*document.onreadystatechanges = () => {
                if (document.readyState == "complete") {
                    this.isloaded = true;
                }
            }*/
       },
       created() {
            this.getGenres();
            this.isLoaded = true;
            
        }

}
</script>

<style scoped lang="scss">
@import '../style/general.scss';

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    background-color: $colorLight;

}

.header_container {

    width: 100vw;
    margin-bottom: 50px;
    
    .header {
        justify-content: left;
        height: 70px;
        color: #24d34e;


        img {
            height: auto;
            max-width: 80%;
            margin:auto;
            
        }

        .select_genre {
            width: 100%;
            background-color: #fff;
        }


    }
}


</style>

