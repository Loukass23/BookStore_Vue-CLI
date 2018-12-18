<template>
    <div>

        <div class="modal fade bs-example-modal-lg" tabindex="-1" role="dialog" aria-labelledby="myLargeModalLabel"
            aria-hidden="true">
            <div class="modal-dialog modal-lg">
                <div class="modal-content">
                    <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel" >
                        
                        <div class="carousel-inner" >
                            <div class="carousel-item " v-for="(book,index) in books" :key="book.id" >
                                <img v-bind:src=books[index].portada alt="Image" class="img-fluid" id="book-img">
                        
                            <div class="carousel-caption d-none d-md-block mt-auto">
                               <h5>{{book.titulo}}</h5> 
                               <p>{{book.descripcion}}</p> 
                            </div>
                            </div>
                             <div class="carousel-item active" >
                                 First
                                <!-- <img v-bind:src=books[index].portada alt="Image" class="img-fluid" id="book-img"> -->
                            </div>
                            
                        </div>
                        <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
                            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                            <span class="sr-only">Previous</span>
                        </a>
                        <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
                            <span class="carousel-control-next-icon" aria-hidden="true"></span>
                            <span class="sr-only">Next</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>


</template>

<script>
    export default {
        name: 'Modal',
        props: {
            books: [],
            position: 0
        }
    }
</script>

<style scoped>
.carousel-inner img{
    opacity: .2;
}
.carousel-caption {
    color: black;
    top : 20px;
}
.carousel-control-next, .carousel-control-prev, .sr-only {
    background-color: rgba(0, 0, 0, 0.342);
}
</style>