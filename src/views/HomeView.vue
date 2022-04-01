<template>
    <div class="home">
        <div class="container overflow-hidden">
            <div class="row gy-5">
                <div class="col-6" v-for="book in books" :key=book.isbn>
                    <div class="card" style="width: 18rem;">
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">{{book.name}}</li>
                            <li class="list-group-item">First author: {{book.author}}</li>
                            <li class="list-group-item">Released: {{book.released}}</li>
                        </ul>
                        <div class="card-footer">
                            <router-link :to="{ name: 'details', params: { id: book.id }}">Read more</router-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HomeView',
    data: () => {
        return {
            books: [],
        }
    },
    mounted() {
        fetch('https://www.anapioficeandfire.com/api/books')
            .then((response) => response.json())
            .then((data) => {
                this.books = []
                data.map((value) => {
                    let segments = value.url.split('/')
                    this.books.push({
                        released: new Date(value.released).toLocaleDateString(),
                        name: value.name,
                        author: value.authors[0],
                        id: segments[segments.length - 1]
                    })
                })
            })
    }
}
</script>
