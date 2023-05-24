<template>
  <div class="card-ui" :class="{ row : cardType === 4 }">
    <figure>
      <img src="../assets/img/logo.webp" />
    </figure>
    <div class="card-ui-textarea">
      <h2 class="card-ui-title">{{ cardData.title }}</h2>
      <p class="card-ui-description">{{ cardData.description }}</p>
      <p class="card-ui-highlight"> {{ cardData }}</p>
    </div>
    <ul class="card-ui-review"> 
      <li class="active"></li>
      <li class="active"></li>
      <li class="active"></li>
      <li></li>
      <li></li>
    </ul>
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
    background-color: #f1f1f1;
  }
  .card-ui.row {
    width: 50%;
    margin-top: 50px;
    display:flex;
  }
  .card-ui.row .card-ui-review {
    display: none;
  }
  .card-ui figure img {
    width: 100%;
  }

  .card-ui-textarea {
    text-align: left;
    box-sizing: border-box;
    padding-left: 10px;
  }
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