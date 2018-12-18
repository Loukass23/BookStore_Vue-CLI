<template>
    <div>
        <div class="modal fade bs-example-modal-lg" tabindex="-1" role="dialog" aria-labelledby="myLargeModalLabel"
            aria-hidden="true">
            <div class="modal-dialog modal-lg">
                <div class="modal-content">
                    <div id="carousel-example-generic" class="carousel slide" data-ride="carousel" v-for="book in books" :key="book.id">
                        <!-- Wrapper for slides -->
                        <div class="carousel-inner">
                            <div class="item">
                                <img v-bind:src=book.portada alt="Image" class="img-fluid" id="book-img"> 
                                <div class="carousel-caption">
                                    {{book.titulo}}
                                </div>
                            </div>
                                <!-- <div class="item">
                            <img class="img-responsive" src="http://placehold.it/1200x600/fffccc/000&text=Two" alt="...">
                            <div class="carousel-caption">
                                Another Image
                            </div>
                        </div>
                        <div class="item">
                            <img class="img-responsive" src="http://placehold.it/1200x600/fcf00c/000&text=Three" alt="...">
                            <div class="carousel-caption">
                                Another Image
                            </div>
                        </div> -->

                        </div>
                    </div>
                                <!-- Controls -->
                                <a class="left carousel-control" href="#carousel-example-generic" role="button"
                                    data-slide="prev">
                                    <span class="glyphicon glyphicon-chevron-left"></span>
                                </a>
                                <a class="right carousel-control" href="#carousel-example-generic" role="button"
                                    data-slide="next">
                                    <span class="glyphicon glyphicon-chevron-right"></span>
                                </a>
                            
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

</style>