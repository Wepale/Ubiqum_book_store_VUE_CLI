<template>
<div class="book">
  <div class="flipContainer">
    <div class="frontCover">
      <img :src="book" alt="Book Cover">
    </div>
    <div class="backCover">
      <h3>{{ someTitle }}</h3>
      <p>{{ someDescription }}</p>
      <button type="button" name="button">Info</button>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Book',
  props: {
    book: String,
    someTitle: String,
    someDescription: String
  }
}
</script>
