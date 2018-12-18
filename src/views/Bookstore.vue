<template>
  <div>
    <div class="container-fluid text-center">
      <div class="row align-items-end" >
        <div class="col-sm-4 ">
          <!-- <img src="..\..\assets\logo.JPG" class="img-fluid" alt="Responsive image"> -->
        </div>
        <div class="col-sm-4 ">
          <h1>Ubiqum Bookstore</h1>
        </div>
        <div class="col-sm-4 ">
          <input type="text" id="myInput" placeholder="search for book title" title="Type in a name" v-model="searchInput">
          <ul id="myUL">
          </ul>
        </div>
      </div>
      <hr>
      <scale-loader v-if="!dataRetrieved"></scale-loader>
      <modal  v-bind:books= books></modal>
      <div class="row">
        <div class="col-sm-12 text-center ">
          <div class="flip flex-container" id="book-container">
          <div v-for="book in searchBook" :key="book.id" class="card" id="book-item">
            
                <div class="face front">
                  <div class="inner flex-item max-width: 50%">
                    
                    <img v-bind:src= book.portada alt="Image" class="img-fluid" id="book-img"> 
                  </div>
                </div>
                <div class="face back">
                  <div class="inner text-center">
                    <h3>{{book.titulo}}</h3>
                    <p id="description">{{book.descripcion}}</p>
                    <button class="btn btn-default" data-toggle="modal" data-target=".bs-example-modal-lg">See more</button>
                    
                  </div>
                
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from '@/components/Modal.vue'
import ScaleLoader from '@/components/ScaleLoader.vue'
  export default {
    name: 'bookstore',
    components: {
Modal,
ScaleLoader
    },
    data() {
      return {
        url: 'https://api.myjson.com/bins/udbm5',
        books: [],
        searchInput: '',
        dataRetrieved: false
      }
    },
    methods: {
      fetchJson(url) {
        return fetch(url).then(function (response) {
            if (response.ok) {
              return response.json();
            }
          }).then((json) => {
            console.log(json.books);
            this.books = json.books;
            this.dataRetrieved = true;

          })
          .catch(console.error("Server Error"));
      }
    },
    created() {
      this.fetchJson(this.url);
    },
    computed: {
       searchBook: function() {
         if (this.dataRetrieved) {
            console.log(this.searchInput.value)      
        return this.books.filter(book => book.titulo.toUpperCase().match(this.searchInput.toUpperCase()) )
         }
         }
      
    }
  }
</script>

<style scoped>

#book-container{
 display: flex;
  flex-direction: row;
 flex-flow: wrap;
  justify-content: center;
 
}
#book-item{
  max-width: 10em;
}
.card{
  -webkit-perspective: 800;   
          perspective: 800;
        position: relative;
        text-align: center;
          -webkit-transform-style: preserve-3d;
    -webkit-transition: 0.5s;
    transform-style: preserve-3d;
    transition: 0.5s;
    background-color: #fff;
}
#book-item:hover {
  -webkit-transform: rotatey(-180deg);
          transform: rotatey(-180deg);

          
}

.flip .card .face {
  -webkit-backface-visibility: hidden ;
    backface-visibility: hidden ;
   z-index: 2;
}


.flip .card .back {
  padding-top: 10%;
  -webkit-transform: rotatey(-180deg);
          transform: rotatey(-180deg);
  position: absolute;
}
.back{
  font-size: x-small;
}
.back h3{
  font-size: small;
}
#description{
  max-height: 100%;
}

</style>