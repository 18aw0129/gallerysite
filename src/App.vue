<template>
  <div id="app">
    <img v-bind:src="require('./assets/' + picURL )" alt="bg" id="bgimg">
    <ol>
      <li v-for="item in items" :key="item.id">
        <img v-bind:src="require('./assets/' + item.url )" v-bind:alt="item.urlalt" v-on:click="changepic($event)">
      </li>
    </ol>
  </div>
</template>

<script>


export default {
  name: 'app',
  data(){
    return{
      items:[
        {"url" : "01s.jpg" , "urlalt" : "01.jpg"},
        {"url" : "02s.jpg" , "urlalt" : "02.jpg"},
        {"url" : "03s.jpg" , "urlalt" : "03.jpg"},
        {"url" : "04s.jpg" , "urlalt" : "04.jpg"}
      ],
      picURL :"01.jpg",
    }
  },
  methods:{
    changepic(event){
      var bgimg = document.getElementById("bgimg");
      bgimg.src = require('./assets/' + event.target.alt);
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  position: fixed;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
#bgimg {
  position: fixed;
  z-index: -999;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
ol{
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 20px;
  width: 80%;
  position: fixed;
  bottom: 0;
  margin: 20px;
}
ol li {
  width: 20%;
}
ol li img {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
}
</style>
