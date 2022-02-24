<template>
  <div class="container header_container">
      <div class="row header col-1">
          <img class="img-fluid" src="../assets/logo-small.svg" alt="">
      </div>

  </div>
</template>

<script>
export default {
    name: 'MyHeader',

}
</script>

<style scoped lang="scss">
@import '../style/general.scss';

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

}

.header_container {
    background-color: #222c36;
    width: 100vw;
    
    .header {
        justify-content: left;
        height: 70px;
        color: #24d34e;


        img {
            border-radius: 50%;
            height: auto;
            max-width: 100%;
            margin:auto;
            
        }
    }
}


</style>

