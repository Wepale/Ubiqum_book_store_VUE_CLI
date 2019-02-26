<template>
  <div class="mainContainer">
    <book :books="myBooks"></book>
  </div>
</template>

<script>
export default {
  name: 'Books_container',
  props: {
    msg: String
  }
}
</script>
