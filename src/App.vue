<template>
 <div id="app">
   <main>
     <div class="search-box">
       <input 
       type="text" 
       class="search-bar" 
       v-model="query" 
       placeholder="Seach..."
       @keypress="showWeather"
       >
     </div>
     <div class="weather-wrapper" v-if="typeof weather.main != 'undefined'">
       <div class="location-box">
         <img src="./assets/germanyf.png"  alt="">
         <div class="location">{{weather.name}} , {{weather.sys.country}}</div>
         <div class="date">{{dateBuilder()}}</div>
       </div>
       <div class="weather-box">
         <div class="temp">{{Math.round(weather.main.temp)}} °C</div>
         <div class="weather">{{weather.weather[0].main}}</div>
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
        api_key: '882bef5a905607d2f5ffd93f02e83beb',
        url: 'api.openweathermap.org/data/2.5/',
        query:'',
        weather:{}
      }
    },
    methods:{
      async showWeather(e){
        if(e.key == 'Enter'){
          let res = await fetch(`${this.url}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          let data = await res.json()
          console.log(data)
        }
      },
     dateBuilder(){
       let d = new Date();
       let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
       let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
       let day = days[d.getDay()];
       let date = d.getDate();
       let month = months[d.getMonth()];
       let year = d.getFullYear();
       return `${day} ${date} ${month} ${year}`;
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
img{
  width: 250px;
  vertical-align: middle;
  height: 100px;
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
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  min-height: 100vh;
  padding: 30px;
  background-image: linear-gradient(to bottom , rgba(0,0,0,.25) , rgba(0,0,0, .6));
}
.search-box{
  width: 45%;
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
.location-box{
 padding: 10px;
 background-color: rgba(255, 255, 255, .25);
 box-shadow: 3px 6px rgba(0,0,0,.25);
 border-radius: 16px;
}
.location-box .location{
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,.25);
}
.location-box .date{
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}
.weather-box{
  text-align: center;
}
.weather-box .temp{
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 100px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0,0,0,.25);
  background-color: rgba(255, 255, 255, .25);
  border-radius: 16px;
  margin: 30px 0;
  box-shadow: 3px 6px rgba(0,0,0,.25);
}
.weather-box .weather{
  padding: 10px;
  background-color: rgba(255, 255, 255, .25);
  box-shadow: 3px 6px rgba(0,0,0,.25);
  border-radius: 16px;
  color: #fff;
  font-size: 28px;
  font-weight: 700;
  text-shadow: 3px 6px rgba(0,0,0,.25);
}
</style>
