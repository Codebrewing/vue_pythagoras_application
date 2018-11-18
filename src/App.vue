<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>현재 컴포넌트 : </h1>
    {{flag}}
    <button @click.prevent="a('Home')">Home</button>
    <button @click.prevent="a('About')">About</button>
    <button @click.prevent="a('Gallery')">Gallery</button>

    <HelloWorld :msg="childData" v-if="!flag" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data(){
    return{
      flag:false,
      title: 'Home',
      childData:null,
      dataSet: {
        Home: [
          {name: 'home 1'}, {name: 'home 2'}, {name: 'home 3'}
        ],
        About: [
          {name: 'About 1'}, {name: 'About 2'}, {name: 'About 3'}
        ],
        Gallery: [
          {name: 'Gallery 1'}, {name: 'Gallery 2'}, {name: 'Gallery 3'}
        ],

      }
    }
  },


  created(){
    setTimeout(()=>{
        this.childData = this.dataSet['Home']
      }, 800)
  },


  methods:{
    a(v){
      this.childData = null
      setTimeout(()=>{
        this.childData = this.dataSet[v]
      }, 800)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
