<template>
  <h1 class="title">과제 1. 카드 UI</h1>
  <section class="ui-module-wrapper">
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

  <h1 class="title">과제 2. 입력 폼 UI</h1>
  <section>
    <!-- default -->
    <article>
      <InputForm :inputLimit="inputLimit" :inputControl="inputControl"/>
    </article>

    <!-- disabled -->
    <article>
      <InputForm :inputLimit="inputLimit" :inputControl="{ isDisabled: true, placeholder: 'disabled 상태'}"/>
    </article>

    <!-- readonly -->
    <article>
      <InputForm :inputLimit="inputLimit" :inputControl="{ isReadOnly: true, placeholder: 'readOnly 상태'}"/>
    </article>
  </section>

</template>

<script>
import InputForm from '@/components/InputForm.vue';
import CardUi from '@/components/CardUi.vue';

export default {
  name: 'App',
  components: {
    CardUi,
    InputForm,
  },
  data() {
    return {
      /**
       * type1 : 세로형 카드 전체 출력,
       * type2 : 세로형 카드 맨 아래 text 미출력,
       * type3 : 세로형 카드 하단 정보부 미출력,
       * type4 : 가로형 카드,
       * score: 별점 범위 1 ~ 5
       */
      cardData : {
        type: Number,
        label:'Card Label',
        title:'Card Title',
        highlightText: 'Highlight',
        crossOut: 'Cross Out',
        score:3,
      },

      inputLimit : {
        // 텍스트 제한 글자 수
        limitCount: 400,
        // 보여줄 초기 값
        remainingCharsCount: 400,
      },

      inputControl: {
        isReadOnly: false,
        isDisabled: false,
        placeholder: '내용을 입력해주세요.',
      }
    }
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  user-select: none;
  font-family: 'Noto Sans KR', sans-serif;
}
.title {
  margin: 30px 0;
}
.ui-module-wrapper {
  width: 89.33%;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
}
.ui-module-wrapper article{
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
