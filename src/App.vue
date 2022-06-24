<template>
  <div class="container">
    <h1 class="title">Ты сегодня покормил кота?</h1>
    <div class="items">
      <cat v-for="cat in items" :cat="cat" :key="cat.id" />
    </div>
  </div>
</template>

<script>
import Cat from './components/Cat.vue';
export default {
  components: { Cat },
  data() {
    return {
      items: [
        {
          id: 1,
          title: 'Сказочное заморское яство',
          name: 'Нямушка',
          taste: 'c фуа-гра',
          portionCount: '10',
          portion: ' порций',
          mousesCount: '',
          mouses: ' мышь в подарок',
          amount: '0,5',
          unit: 'кг',
          selected: 'Печень утки разварная с артишоками',
          disabled: false,
          distext: 'Печалька, с фуа-гра закончился.',
        },
        {
          id: 2,
          title: 'Сказочное заморское яство',
          name: 'Нямушка',
          taste: 'c рыбой',
          portionCount: '40',
          portion: ' порций',
          mousesCount: '2',
          mouses: ' мыши в подарок',
          amount: '2',
          unit: 'кг',
          selected: 'Головы щучьи с чесноком да свежайшая сёмгушка.',
          disabled: false,
          distext: 'Печалька, с рыбой закончился.',
        },
        {
          id: 3,
          title: 'Сказочное заморское яство',
          name: 'Нямушка',
          taste: 'с курой',
          portionCount: '100',
          portion: ' порций',
          mousesCount: '5',
          mouses: ' мышей в подарок заказчик доволен',
          amount: '5',
          unit: 'кг',
          selected: 'Филе из цыплят с трюфелями в бульоне.',
          disabled: true,
          distext: 'Печалька, с курой закончился.',
        },
      ],
    };
  },
};
</script>

<style>
.title {
  font-family: 'Exo 2.0 Thin', sans-serif;
  color: #fff;
  font-size: 36px;
  line-height: 44px;
  font-weight: 100;
  text-shadow: 0px 1px 1px #000000;
  text-align: center;
  margin-bottom: 20px;
}
.items {
  font-family: 'Trebuchet MS', sans-serif;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.container {
  margin: 0 auto;
  max-width: 1120px;
  position: relative;
  top: 50vh;
  left: 0;
  transform: translate(0, -50%);
}

/* responsive */

@media screen and (max-width: 1160px) {
  .container {
    max-width: 750px;
    top: 65vh;
  }
}
@media screen and (max-width: 750px) {
  .container {
    max-width: 500px;
    top: 100vh;
  }
}
</style>
