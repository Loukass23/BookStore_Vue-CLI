<template>
    <div>
        
<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" ref="modal" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
    
      <div class="modal-body">
         <div id="bookCarousel" class="carousel slide" data-ride="carousel" data-pause="hover">

                        <div ref="carousel_inner" class="carousel-inner ">
                            
                            <div v-if="index == position" class="carousel-item active" v-for="(book,index) in books" :key="book.id">
                                <img v-bind:src=books[index].portada alt="Slide index" class="img-fluid" >

                                <div class="carousel-caption mt-auto">
                                    <h5>{{book.titulo}}</h5>
                                    <p>{{book.descripcion}}</p>
                                </div>
                            </div>

                            <div v-else class="carousel-item">
                                <img v-bind:src=books[index].portada alt="Slide index" class="img-fluid" >

                                <div class="carousel-caption mt-auto">
                                    <h5>{{book.titulo}}</h5>
                                    <p>{{book.descripcion}}</p>
                                </div>
                            </div>


                        
                        </div>
                        <a class="carousel-control-prev" href="#bookCarousel" role="button" data-slide="prev">
                            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                            <span class="sr-only">Previous</span>
                        </a>
                        <a class="carousel-control-next" href="#bookCarousel" role="button" data-slide="next">
                            <span class="carousel-control-next-icon" aria-hidden="true"></span>
                            <span class="sr-only">Next</span>
                        </a>
                    </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        
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
            books: null,
            position: 0
        },
        mounted(){
            let modal = this.$refs.modal
            $(this.$refs.modal).one('hidden.bs.modal', function (e) {
 console.log("out")});
    console.log(this.$refs.modal)
   
}
    }
</script>

<style scoped>
    .carousel-inner img {
        opacity: .2;
        max-width: 80%;
    }

    .carousel-caption {
        color: black;
        top: 20px;
    }

    .carousel-control-next,
    .carousel-control-prev {
        background-color: rgba(0, 0, 0, 0.192);

    }

    .modal-dialog {
   
    top: 2%;
    padding: 2%;
  transform: translate(-50%, -50%);
       
    }
  
        
    

</style>