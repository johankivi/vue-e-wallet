<template>
  <section class="card-form">
    <label for="number" class="col-2">Card Number</label>
    <input type="text" name="number" class="col-2" v-model="card.cardNumber" maxlength="16" @keyup="updateCard" placeholder="XXXX XXXX XXXX XXXX">
    <label for="cardholder" class="col-2">Cardholder Name</label>
    <input type="text" name="cardholder" class="col-2" v-model="card.cardHolder" @keyup="updateCard" placeholder="Firstname Lastname">
    <label for="month" class="col-1">Month</label>
    <label for="year" class="col-1">Year</label>
    <select name="month" v-model="card.validUntil.month" class="col-1" @change="updateCard">
        <option value="01">01</option>
        <option value="02">02</option>
        <option value="03">03</option>
        <option value="04">04</option>
        <option value="05">05</option>
        <option value="06">06</option>
        <option value="07">07</option>
        <option value="08">08</option>
        <option value="09">09</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
    </select>
    <select name="month" v-model="card.validUntil.year" class="col-1" @change="updateCard">
        <option value="21">21</option>
        <option value="22">22</option>
        <option value="23">23</option>
        <option value="24">24</option>
        <option value="25">25</option>
    </select>
    <label for="vendor" class="col-2">Vendor</label>
    <select name="vendor" class="col-2" v-model="card.vendor" @change="updateCard">
        <option value="Bitcoin Inc">Bitcoin Inc</option>
        <option value="Blockchain Inc">Blockchain Inc</option>
        <option value="Evil Corp">Evil Corp</option>
        <option value="Ninja Bank">Ninja Bank</option>
    </select>
  </section>
</template>

<script>
export default {
  name: 'CardForm',
  props: {
    cardData: Object
  },
  data () {
    return {
      card: {
        vendor: 'Blank',
        cardHolder: '',
        cardNumber: '',
        validUntil: {
          year: 'YY',
          month: 'MM'
        }
      }
    }
  },
  methods: {
    validFormatter () {
      if (this.card.validUntil.length === 2) {
        this.card.validUntil += '/'
      }
    },
    updateCard () {
      let card = {
        vendor: this.card.vendor,
        cardHolder: this.card.cardHolder,
        cardNumber: this.cardNumberFormatted,
        validUntil: this.card.validUntil
      }

      this.$emit('updatecard', card)
    }
  },
  computed: {
    cardNumberFormatted () {
      let numberChunks = this.card.cardNumber.match(/.{1,4}/g)
      if (numberChunks) {
        return numberChunks.join(' ')
      } else {
        return ''
      }
    }
  }
}
</script>

<style>
.card-form {
    margin: 2rem 0 0 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0 1rem;
}

.card-form label {
    padding: .25rem 0;
    font-size: .7rem;
    text-transform: uppercase;
}

.card-form input, select {
    border: 1px solid black;
    border-radius: .25rem;
    padding: .5rem;
    height: 2.6rem;
    margin: 0 0 .8rem 0;
    box-sizing: border-box;
    font-size: 1rem;
    width: 100%;
}

.col-1 {
    grid-column: auto / span 1;
}

.col-2 {
    grid-column: auto / span 2;
}

</style>
