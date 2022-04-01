<template>
  <div class="container">
  <div class="row g-2" v-if="book">
    <div class="col-6">
      <div class="p-3 border bg-light">Name</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">{{ book.name }}</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">Authors</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">{{ book.author }}</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">Page number</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">{{ book.numberOfPages }}</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">Character number</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">{{ book.characters.length }}</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">Publisher</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">{{ book.publisher }}</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">Country</div>
    </div>
    <div class="col-6">
      <div class="p-3 border bg-light">{{ book.country }}</div>
    </div>
  </div>
</div>
</template>

<script>
import { useRoute } from 'vue-router'

export default {
  name: 'DetailsView',
  data() {
    return {
      book: null,
    }
  },
  mounted() {
    fetch('https://www.anapioficeandfire.com/api/books/' + useRoute().params.id)
      .then((response) => response.json())
      .then((data) => {
        this.book = data
        this.book.author = data.authors.join(',')
      })
  }
}
</script>
