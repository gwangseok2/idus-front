<template>
  <div class="card-ui" :class="[ cardData ? `type${cardData.type}` : '']">
    <figure>
      <img src="../assets/img/logo.webp" />
    </figure>
    <div class="card-ui-bottom">
      <div class="card-ui-textarea">
        <div class="card-ui-label">{{ cardData.label }}</div>
        <h2 class="card-ui-title">{{ cardData.title }}</h2>
        <p class="card-ui-description">{{ cardData.description }}</p>
        <!-- <p class="card-ui-highlight"> {{ cardData }}</p> -->
      </div>
      <ul class="card-ui-review"> 
        <li class="active"></li>
        <li class="active"></li>
        <li class="active"></li>
        <li></li>
        <li></li>
      </ul>
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
    width: 23%;
    margin: 0 10px;
    border: 1px solid #ccc;
    min-height: 100px;
  }
  /** 
    type1 : asdsad,
    type2 : asdsad,
    type3 : asdasd,
    type4 : 가로형 카드
  **/
  .card-ui.type4 {
    width: 50%;
    margin-top: 50px;
    display:flex;
  }
  .card-ui.type4 .card-ui-review {
    display: none;
  }
  .card-ui figure img {
    width: 100%;
  }

  .card-ui-bottom {
    width: 100%;
    padding: 5px 0;
    background-color: #f4f4f4;
  }
  /* card-ui-textarea */
  .card-ui-textarea {
    text-align: left;
    box-sizing: border-box;
    padding-left: 10px;
  }
  .card-ui-textarea .card-ui-label {
    font-size: min(1.126760vw, 16px);
    color: #c8c8c8;
  }
  .card-ui-textarea .card-ui-title {
    margin-top: 5px;
    font-size: min(1.2676056vw, 18px);
    color: #000;
  }

  
  /* //card-ui-textarea */

  .card-ui-review {
    border-top: 1px solid #111;
    display: flex;
    margin: 10px 0;
    padding: 15px 0 15px 10px;
    gap: 5px;
    list-style: none;
  }
  .card-ui-review li{
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: #c8c8c8;
  }
  .card-ui-review li.active {
    background-color: orange;
  }

  
</style>