<template>
  <main id="home">
    <Top :title="title" :cardType="cardType"/>
    <Card :cardData="activeCard" />
    <CardStack :cards="cards" v-on:setactivecard="setActiveCard" />
    <a href="#" class="cta" @click="toggleView">Add New Card</a>
  </main>
</template>

<script>
import Top from './Top'
import Card from './Card'
import CardStack from './CardStack'

export default {
  name: 'Home',
  props: {
    cards: Array,
    activeCard: Object
  },
  components: {
    Top,
    Card,
    CardStack
  },
  data () {
    return {
      title: 'E-wallet',
      cardType: 'active card'
    }
  },
  methods: {
    toggleView () {
      this.$emit('toggleview')
    },
    setActiveCard (card) {
      this.$emit('setactivecard', card)
    }
  }
}
</script>

<style>

a.cta {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 4rem;
  font-size: 1.2rem;
  text-transform: uppercase;
  font-weight: 700;
  text-decoration: none;
  color: black;
  border: .125rem solid black;
  box-sizing: border-box;
  border-radius: .5rem;
  margin: 2rem 0;
}

a.cta:hover {
  background: #000;
  color: #ddd;
}

a.cta:active {
  background: #000;
  color: #FFF;
}

</style>
