<template>
  <div class="card-ui" :class="[ cardData ? `type${cardData.type}` : '']">
    <figure class="card-ui-img">
      <img src="../assets/img/idus_logo2.png" />
    </figure>
    <div class="card-ui-bottom">
      <div class="card-ui-textarea">
        <div class="card-ui-label">{{ cardData.label }}</div>
        <h2 class="card-ui-title">{{ cardData.title }}</h2>
        <div class="card-ui-highlight">
          <span class="card-ui-highlight-text">{{  cardData.highlightText }}</span>
          <span class="card-ui-highlight-crossout">{{  cardData.crossOut }}</span>
        </div>
      </div>
      <template v-if="cardData.type !== 3">
        <ul class="card-ui-review"> 
          <li v-for="index in 5" :key="index" :class="[ cardData.score >= index ? 'active' : '']"></li>
        </ul>
        <div v-if="cardData.type === 1" class="card-ui-review-text">Lorem ipsum dolor sit amet...</div>
      </template>
    </div>
  </div>
</template>

<script>
  export default {
    props:{
      cardData: Object,
    },
    data() {
      return {
        cardType: Number,
      }
    },
    created() {
      this.cardType = this.cardData.type;
    },  
  }
</script>

<style scoped>
  .card-ui {
    display:inline-block;
    width: 100%;
    border: 1px solid #ccc;
    min-height: 100px;
  }
  .card-ui-img {
    overflow: hidden;
    background-color: #EE6000;
  }
  .card-ui-img img {
    width: 100%;
    display: block;
  }
  /** 
    type1 : 세로형 카드 전체 출력,
    type2 : 세로형 카드 맨 아래 text 미출력,
    type3 : 세로형 카드 하단 정보부 미출력,
    type4 : 가로형 카드
  **/
  .card-ui.type4 {
    width: 100%;
    margin-top: 50px;
    display:flex;
  }
  .card-ui.type4 .card-ui-review {
    border-top:none;
  }

  .card-ui-bottom {
    width: 100%;
    padding: 5px 0;
    background-color: #F8F9FB;
  }

  /* card-ui-textarea */
  .card-ui-textarea {
    width: 100%;
    text-align: left;
    box-sizing: border-box;
    padding-left: 10px;
  }
  .card-ui-textarea .card-ui-label {
    font-size: min(2.26760vw, 16px);
    color: #acacac;
  }
  .card-ui-textarea .card-ui-title {
    margin-top: 5px;
    font-size: min(2.2676056vw, 18px);
    color: #000;
  }
  /* //card-ui-textarea */

  /* card-ui-highlight */
  .card-ui-highlight {
    margin: 30px 0 10px 0;
    font-size: min(2.06760vw, 14px);
  }
  .card-ui-highlight .card-ui-highlight-text {
    color: #EE6000;
    font-weight: 500;
    margin-right: 5px;
  }
  .card-ui-highlight .card-ui-highlight-crossout {
    color: #c1c2c3;
    position: relative;
    letter-spacing: -0.75px;
    font-size: min(1.86760vw, 12px);
  }

  .card-ui-highlight .card-ui-highlight-crossout::after {
    content:"";
    position: absolute;
    display:block;
    top:60%;
    left:0;
    width: 100%;
    height: 1px;
    transform: translateY(-50%);
    background-color: #a9a9a9;
  }
  /* //card-ui-highlight */

  /* card-ui-review */
  .card-ui-review {
    border-top: 1px solid rgba(1,1,1,0.2);
    display: flex;
    padding: 15px 0 10px 10px;
    gap: 5px;
    list-style: none;
  }
  .card-ui-review li{
    width: 0.9765625vw;
    height: 0.9765625vw;
    min-width: 10px;
    min-height: 10px;
    border-radius: 50%;
    background-color: #c8c8c8;
  }
  .card-ui-review li.active {
    background-color: orange;
  }
  .card-ui-review-text {
    text-align: left;
    padding-left: 10px;
    font-size: min(2.26760vw, 16px);
  }
  /* //card-ui-review */

  
</style>