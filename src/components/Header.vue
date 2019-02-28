<template>
<div class="header">
  <div class="headerLeft">
    <div class="logo">
    <img src="../assets/ubiqum_logo.png" alt="Book Store Logo">
    <h1>Ubiqum Book Store</h1>
  </div>
  </div>
  <div class="headerRight">
    <div class="input">
      <label for="findBox">Search:</label>
      <input id="findBox" type="text" ref="searchBox" :value="someText" @input="handleInput">
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    value: String
  },
  data () {
    return {
      someText: ""
    }
  },
  //V-model works different on components. We need to emit the value of the imput
  methods: {
    handleInput (e) {
      this.$emit('input', this.$refs.searchBox.value)
    }
  }
}
</script>
