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
      <label for="findBox">Find a book:</label>
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
  methods: {
    handleInput (e) {
      this.$emit('input', this.$refs.searchBox.value)
    }
  }
}
</script>
