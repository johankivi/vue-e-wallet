<template>
  <section class="card-stack">
      <Card v-for="(card, ind) in cards" :key="ind" :cardData="card" v-on:setactivecard="$emit('setactivecard', card)" />
  </section>
</template>

<script>
import Card from './Card'

export default {
  name: 'CardStack',
  components: {
    Card
  },
  props: {
    cards: Array
  }
}
</script>

<style>
 .card-stack {
     margin: 2rem 0 12rem 0;
     display: grid;
     grid-auto-rows: 4rem;
 }

</style>
