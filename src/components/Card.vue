<template>
  <article class="card" :class="vendorClass" v-on:click="setActiveCard">
      <header>
        <img v-if="cardData.vendor == 'Bitcoin Inc'" src="@/assets/chip-dark.svg" alt="chip">
        <img v-if="cardData.vendor !== 'Bitcoin Inc'" src="@/assets/chip-light.svg" alt="chip">
        <img v-if="cardData.vendor == 'Evil Corp'" src="@/assets/vendor-evil.svg" alt="Evil Corp">
        <img v-if="cardData.vendor == 'Blockchain Inc'" src="@/assets/vendor-blockchain.svg" alt="Blockchain Inc">
        <img v-if="cardData.vendor == 'Ninja Bank'" src="@/assets/vendor-ninja.svg" alt="Ninja Bank">
        <img v-if="cardData.vendor == 'Bitcoin Inc'" src="@/assets/vendor-bitcoin.svg" alt="Bitcoin Inc">
      </header>
      <section class="number">
          {{ cardData.cardNumber }}
      </section>
      <section class="info">
          <aside class="holder">
              <span>Cardholder Name</span>
              <p>{{ cardData.cardHolder }}</p>
          </aside>
          <aside class="valid">
            <span>Valid until</span>
              <p>{{ cardData.validUntil.month }}/{{ cardData.validUntil.year }}</p>
          </aside>
      </section>
  </article>
</template>

<script>
export default {
  name: 'Card',
  props: {
    cardData: Object
  },
  data () {
    return {

    }
  },
  methods: {
    setActiveCard () {
      if (this.cardData.vendor !== 'Blank') {
        this.$emit('setactivecard', this.cardData)
      }
    }
  },
  computed: {
    vendorClass () {
      switch (this.cardData.vendor) {
        case 'Evil Corp' :
          return 'evil'
        case 'Bitcoin Inc' :
          return 'bitcoin'
        case 'Ninja Bank' :
          return 'ninja'
        case 'Blockchain Inc' :
          return 'blockchain'
        case 'Blank' :
          return 'blank'
      }
    }
  }
}
</script>

<style>
.card {
    max-width: 24rem;
    height: 14rem;
    border-radius: .6rem;
    background: #eee;
    padding: 1rem;
    box-sizing: border-box;
    box-shadow: 0 0 .5rem rgba(0, 0, 0, 0.4);
    display: grid;
    gap: .5rem 0;
    grid-template-columns: 1fr 1fr;
    grid-auto-rows: 2.8rem;
    text-shadow: -1px -1px 2px rgba(255, 255, 255, .4);
}

.evil {
    background: linear-gradient(248.3deg, rgba(0, 0, 0, 0.16) 0%, rgba(0, 0, 0, 0) 100%), #F33355;
    color: white;
}

.blockchain {
    background: linear-gradient(248.52deg, rgba(0, 0, 0, 0.15) 1.49%, rgba(0, 0, 0, 0) 100%), #8B58F9;
    color: white;
}

.bitcoin {
    background: linear-gradient(248.04deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 99.07%), #FFAE34;
    color: #222;
}

.ninja {
    background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 100%), #222222;
    color: white;
}

.blank {
    background: linear-gradient(237.75deg, rgba(255, 255, 255, 0.24) 0%, rgba(255, 255, 255, 0) 100%), #D0D0D0;
}

.card header {
    display: flex;
    grid-column: auto / span 2;
    grid-row: auto / span 2;
    justify-content: space-between;
    align-items: flex-start;
}

.card header img {
    opacity: .8;
}

.card header [alt="chip"] {
    align-self: flex-end;
    opacity: 1;
}

.card section.number {
    grid-column: auto / span 2;
    grid-row: auto / span 1;
    display: flex;
    font-size: 1.6rem;
    letter-spacing: .05rem;
    padding: .5rem 0 0 0;
    text-transform: uppercase;
}

.card section.info {
    display: flex;
    grid-column: auto / span 2;
    grid-row: auto / span 1;
}

.card section aside span {
    display: block;
    text-transform: uppercase;
    font-size: .7rem;
    margin: 0 0 .25rem 0;
}

.card section aside.valid span {
    text-align: right;
}

.card section aside p {
    display: block;
    text-transform: uppercase;
    margin: 0;
    padding: 0;
}

.card section aside.valid p {
    text-align: right;
}

.card section.info aside.holder {
    flex: 1;
}

</style>
