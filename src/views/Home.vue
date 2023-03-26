<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <counter/>
    <counter-squared/>
    <div class="buttons">
      <button @click="$store.dispatch('decreaseCounter')">-</button>
      <button @click="$store.dispatch('increaseCounter')">+</button>
    </div>
    <div>
      <input placeholder="Enter color code" type="text" v-model="colorCode">
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
    counter: require('@/components/Counter.vue').default,
    counterSquared: require('@/components/CounterSquared.vue').default,
  },
  computed: {
    colorCode: {
      get() {
        return this.$store.state.colorCode
      },
      set(newValue) {
        this.$store.dispatch('setColorCode', newValue)
      }
    }
  }
}
</script>

<style>
  div {
    margin-bottom: 10px;
  }
  .counter {
    font-size: 80px;
  }
  .buttons button {
    font-size: 40px;
    width: 100px;
    margin: 0 10px;
    cursor: pointer;
  }
</style>