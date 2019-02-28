<template>
<div class="mainHeader">
  <app-header v-model="userSearch"></app-header>
  <div class="booksContainer">
    <div v-if="!myBooks.length && isLoaded" class="noResults">
      <h2>No results</h2>
    </div>
    <book v-for="item of myBooks" :key="item.title" :book="item.cover" :someTitle="item.title" :someDescription="item.description"></book>
  </div>
</div>
</template>

<script>
import Header from './components/Header.vue'
import Book from './components/Book.vue'

export default {
  name: 'app',
  components: {
    "app-header": Header,
    "book": Book,
  },
  data() {
    return {
      MY_BOOKS: [],
      myBooks: [],
      userSearch: "",
      isLoaded: false
    }
  },
  methods: {
    async getData() {
      //await the response of the fetch call
      let response = await fetch("https://api.myjson.com/bins/zyv02", {
        method: "GET",
        dataType: 'json',
      });
      //proceed once the first promise is resolved.
      let data = await response.json()
      //proceed only when the second promise is resolved

      this.myBooks = this.MY_BOOKS = data.books;
      window.console.log(this.myBooks);
      this.isLoaded = true;
    },
  },
  watch: {

    /*
     * This function filter the books if the tittle or description includes the user input
     */

    userSearch() {
      if (this.userSearch.length) {
        this.myBooks = this.MY_BOOKS.filter(book => book.title.toLowerCase().includes(this.userSearch.toLowerCase()) ||
          book.description.toLowerCase().includes(this.userSearch.toLowerCase()));
      } else {
        this.myBooks = this.MY_BOOKS;
      }
    }
  },
  //Fetch call
  created() {
    this.getData();
  },
}
</script>
