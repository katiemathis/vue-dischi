<template>
          <select class="debug m-4 select_genre">
            <option value="">Genre</option>
            <option v-for="(genre, index) in genreItems" 
            :key="index"
            :value= "MyGenres.genre" >{{MyGenres.genre}}
            </option>

          </select>
  
</template>

<script>

const axios = require('axios');

export default {
        name: 'MySelectors',
        props: {
          "MyGenres": Object
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

<style>

</style>