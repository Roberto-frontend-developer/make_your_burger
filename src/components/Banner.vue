<template>
 <div id="main-banner">
  <h1>Make Your burger</h1>
 </div>
</template>
<script>
 export default {
  name:'Banner'
 }
</script>
<style scoped>
#main-banner {
 background-image: url('/public/img/burger.jpg');
 background-position: 0 -230px;
 background-size: cover;
 height: 500px;

 display: flex;
 align-items: center;
 justify-content: flex-start;
}


#main-banner  h1 {

 text-align: center;
 font-size: 60px;
 color: white;
 background-color: #222;
 border-radius: 0 8px 8px 0;
 padding: 20px 40px;

}

</style>
