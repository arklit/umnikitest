<template>
  <div class="beer">
    <img class="beer__img" src="@/images/pivo.jpg"/>
    <div class="beer__info">
      <p class="beer__title">Ваше пиво на сегодня:</p>
      <p class="beer__brand beer__item">{{beerBrand}}</p>
      <p class="beer__name beer__item">{{beerName}}</p>
      <p class="beer__grade beer__item">{{alcohol}}</p>
      <button class="beer__button" @click="getBear">хочу другое</button>
    </div>
  </div>
</template>
<script>
export default {
   props: [
     "beerBrand", "beerName", "alcohol", "getBear"
   ],
}
</script>
<style scoped>
.beer {
  padding: 20px;
  display: flex;
}
.beer__img {
  width: 300px;
  height: 400px;
  margin-top: 50px;
}
.beer__info {
  width: 100%;
  padding: 15px;
  margin-top: 50px;
  border: 1px solid #c2c2c2;
}
.beer__title {
  font-size: 26px;
  text-align: center;
}
.beer__brand::before {
  content: "Brand:";
  margin-right: 10px;
}
.beer__name::before {
  content: 'Name:';
  margin-right: 10px;
}
.beer__grade::before {
  content: 'Alcohol:';
  margin-right: 10px;
}
.beer__item {
  margin-top: 45px;
  margin-left: 15px;
  font-size:  24px;
}
.beer__button {
  border: 1px solid #c2c2c2;
  outline: none;
  background-color: transparent;
  border-radius: 10%;
  padding: 5px;
  margin: 10px 0 0 15px;
  cursor: pointer;
}
@media screen and (max-width: 1000px) {
  .beer__img {
    width: 200px;
    height: 300px;
  }
  .beer__item {
    margin-left: 0;
  }
  .beer__title {
    font-size: 20px;
  }
  .beer__item {
    font-size: 20px;
  }
  .beer__button {
    margin-left: 0;
  }
}
@media screen and (max-width: 650px) {
  .beer__img {
    display: none;
  }
  .beer__title {
    font-size: 18px;
  }
  .beer__item {
    font-size: 18px;
    margin-top: 20px;
  }

}
</style>