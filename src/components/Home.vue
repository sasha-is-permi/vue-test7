<template> 
<div>

   
    <section class="section-doc">
        <div class="container cont-doc">
            <div class="row">
                <div class=" col content-doc">
                    <div class="cont-doc-text" id="doc-text">
                        <h2>Документы</h2>
                    </div>
                    <div class="cont-management">
                        <div class="cont-bookmark paragraph-indent" id="bookmark">
                            <img src="../assets/bookmark.svg"/>
                        </div>
                        <div class="cont-new-type paragraph-indent" id="new-type">
                            <div class="new-type-icon plus">
                                <img src="../assets/icon-plus.svg"/>
                            </div>
                            <div class="new-type-text">
                                <p>Новый тип</p>
                            </div>
                        </div>
                        <div class="cont-new-doc paragraph-indent" id="new-doc">
                            <div class="new-doc-icon plus">
                                <img src="../assets/icon-plus.svg"/>
                            </div>
                            <div class="new-doc-text">
                                <p>Новый документ</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-5">
                    <div class="cont-form-search">
                        <form class="form-search ">
                            <div class="input-group mt-3">
                                <span class="input-group-text" id=search>
                                    <img src="../assets/icon-search.svg"/>
                                </span>
                                <input v-model="doc" id="search" type="text" name="search" placeholder="Документы для сборщиков" class="form-control">
                                <!-- Показываем крестик только если что-то введено кроме пробелов
                                  При клике на крестик поле ввода очищается -->
                                <span v-show="doc.trim() !== ''"   @click="doc=''" class="input-group-text" id="close">
                                    <img src="../assets/icon-close.svg"/>
                                </span>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>




</div>
</template>


<script>
   export default{
     data(){
         return{
             doc:""
         }
     }
   }
</script>


   

<style scoped>

.content-doc {
    
    display: flex;
    margin-top: 2rem;
    justify-content: space-between;
}
.cont-doc-text h2 {
    font-size: 22px;
    margin-bottom: 0;
    
}
.cont-management {
    display: flex;
}
.cont-bookmark {
    border: 1px solid #BFC9E0;
    border-radius: 50px;
}

.cont-bookmark img {
    padding: 8px 10px;
    
}
.cont-bookmark:hover {
    cursor: pointer;
    box-shadow: 0px 3px 3px rgb(0, 0, 0, 20%);
    transition-duration: 0.3s;
}
.cont-new-type {
    display: flex;
    border: 1px solid #BFC9E0;
    border-radius: 20px;
}
.cont-new-doc {
    display: flex;
    border: 1px solid #BFC9E0;
    border-radius: 20px;
}

.cont-new-type:hover {
    cursor: pointer;
    box-shadow: 0px 3px 3px rgb(0, 0, 0, 20%);
    transition-duration: 0.3s;
}
.cont-new-doc:hover {
    cursor: pointer;
    box-shadow: 0px 3px 3px rgb(0, 0, 0, 20%);
    transition-duration: 0.3s;
}
.new-type-text p, .new-doc-text p {
    margin-bottom: 0;
    padding-right: 20px;
}
.paragraph-indent {
    margin-left: 30px;
}


.plus {
    padding: 0 10px 0 10px;
}



#search {
    border: none;
}

.input-group-text {
    background-color: #fff;
    border: none;
    
}
.input-group-text:first-child {
    padding-left: 0;
}
.input-group {
    border-bottom: 1px solid #BFC9E0;
}


</style>