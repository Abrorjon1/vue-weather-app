<template>
   <div id="app">
     <main>
       <div class="search-box">
         <input type="text" class="search-bar" placeholder="Seach...">
       </div>

       <div class="weather-wrapper">
         <div class="location-box">
           
         </div>
       </div>
     </main>
   </div>
</template>

<script>
  export default{
    name:'App',
    data(){
      return{
        api_key: '882bef5a905607d2f5ffd93f02e83beb'
      }
    }
  }
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  font-family: 'montserrat', sans-serif;
}
#app{
  background-image: url('./assets/nature.jpg');
  background-size: cover;
  background-position: center;
  transition: .4s ;
}
main{
  min-height: 100vh;
  padding: 30px;
  background-image: linear-gradient(to bottom , rgba(0,0,0,.25) , rgba(0,0,0, .6));
}
.search-box{
  width: 90%;
  padding: 10px;
}
.search-box .search-bar{
  padding: 15px;
  width: 100%;
  color: #353535;
  font-size: 20px; 
  border: none;
  background-color: rgba(255, 255, 255, .5);
  outline: none;
  appearence: none;
  border-radius: 0 16px 0 16px;
  transition: .4s;
}

.search-box .search-bar:hover, .search-box .search-bar:focus{
 box-shadow: 0 0 16px rgba(0, 0, 0, .25);
 background-color: rgba(255, 255, 255, .75);
  border-radius:16px 0 16px 0;

}
</style>
