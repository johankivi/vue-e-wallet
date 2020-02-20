<template>
  <header class="top">
      <h1>{{ title }}</h1>
      <p class="card-type">{{ cardType }}</p>
  </header>
</template>

<script>
export default {
  name: 'Top',
  props: {
    title: String,
    cardType: String
  },
  data () {
    return {

    }
  }
}
</script>

<style>
.top {
    display: flex;
    flex-direction: column;
    text-transform: uppercase;
}

.top h1 {
    flex: 2;
    text-align: center;
    line-height: 2rem;
    font-size: 2rem;
    margin: 0;
    padding: 1.5rem 0;

}

.top p {
    flex: 1;
    text-align: center;
    font-size: .8rem;
    font-weight: 600;
    color: rgba(0,0,0,.4);
    margin: 0;
    padding: .25rem;
}
</style>
