<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Hello Vue3 TV"/>
  <CardUi :cardData="{...cardData, type:1}" /> 
  <CardUi :cardData="{...cardData, type:2}" /> 
  <CardUi :cardData="{...cardData, type:3}" /> 
  <CardUi :cardData="{...cardData, type:4}" /> 
</template>

<script>
import CardUi from '@/components/CardUi.vue';
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    CardUi,
  },
  data() {
    return {
      cardData :{
        type: Number,
        title:'card',
        description: '미쳣다 컴포넌트',
      }
    }
  },
}
</script>

<style>
* {
  margin:0;
  padding:0;
  user-select: none;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
