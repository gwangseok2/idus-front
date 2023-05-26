<template>
  <h1 class="title">과제 1</h1>
  <section class="module-wrapper">
    <article>
      <CardUi :cardData="{...cardData, type:1}" /> 
    </article>

    <article>
      <CardUi :cardData="{...cardData, type:2}" /> 
    </article>
    
    <article>
      <CardUi :cardData="{...cardData, type:3}" /> 
    </article>

    <article>
      <CardUi :cardData="{...cardData, type:4}" /> 
    </article>
  </section>

</template>

<script>
import CardUi from '@/components/CardUi.vue';

export default {
  name: 'App',
  components: {
    CardUi,
  },
  data() {
    return {
      cardData : {
        type: Number,
        label:'Card Label',
        title:'Card Title',
        highlightText: 'Highlight',
        crossOut: 'Cross Out'
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
  font-family: 'Noto Sans KR', sans-serif;
}
.title {
  margin: 30px 0;
}
.module-wrapper {
  width: 89.33%;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
}
.module-wrapper article{
  max-width: 420px;
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
