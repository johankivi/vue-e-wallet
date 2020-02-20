<template>
  <main id="add-card">
    <Top :title="title" :cardType="cardType"/>
    <Card
      :cardData="card"
    />
    <CardForm @updatecard="updateCard" />
    <a href="#" class="cta" @click="addCard">Add Card</a>
  </main>
</template>

<script>
import Top from './Top'
import Card from './Card'
import CardForm from './CardForm'

export default {
  name: 'AddCard',
  components: {
    Top,
    Card,
    CardForm
  },
  data () {
    return {
      title: 'Add new card',
      cardType: 'New card',
      card: {vendor: 'Blank', cardHolder: '', cardNumber: '', validUntil: {year: 'YY', month: 'MM'}}
    }
  },
  methods: {
    updateCard (updatedCard) {
      this.card = updatedCard
    },
    addCard () {
      this.$emit('addcard', this.card)

      // empty card
      this.card = {vendor: 'Blank', cardHolder: '', cardNumber: '', validUntil: {year: 'YY', month: 'MM'}}
      this.$emit('toggleview')
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
