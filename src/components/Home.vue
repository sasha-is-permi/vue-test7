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


  
            <div class="row">
                <div class="col-5">
                    <div class="accordion">
                        <div class="accordion-item" v-for="category in categoryes" :key="category.id">
                            <input class="accordion-item-input" type="checkbox" :id="'accordion-'+category.id"/>
                            <label class="accordion-item-triger" :for="'accordion-'+category.id">
                                <div class="accordion-block">
                                    <div class="accordion-block-text">
                                        <div class="accordion-icon-arrow">
                                            <img src="../assets/icon-down-arrow.svg"/>
                                        </div>
                                        <div class="accordion-text-h">
                                            <h3>{{category.name}}</h3>
                                        </div>
                                        <div class="accordion-icon-circle" v-if="category.requied">
                                            <img src="../assets/icon-circle-color.svg"/>
                                        </div>
                                        <div class="accordion-text-p">
                                            <p>{{category.description}}</p>
                                        </div>
                                    </div>
                                    <div class="accordion-block-icon">
                                        <div class="accordion-icon-manager">
                                            <img src="../assets/icon-edit.svg"/>
                                        </div>
                                        <div class="accordion-icon-manager">
                                            <img src="../assets/icon-delete.svg"/>
                                        </div>
                                        <div class="accordion-icon-manager">
                                            <img src="../assets/icon-reverse.svg"/>
                                        </div>
                                    </div>

                                </div>

                            </label>
                            <div class="accordion-item-content" v-for="document in documents1"  v-show="document.categoryId==category.id" :key="document.key">
                                <div class="accordion-item-block"  v-if="document.categoryId==category.id">
                                    <div class="accordion-item-block-text">
                                        <div class="accordion-item-h">
                                            <h4>{{document.name}}</h4>
                                        </div>
                                        <div class="accordion-icon-elipse" v-if="category.requied">
                                            <img src="../assets/icon-ellipse-blue.svg"/>
                                        </div> 
                                        <div class="accordion-text-pink" v-if="category.requied" >
                                            <p>Обязательный</p>
                                        </div>
                                        <div class="accordion-text-p" v-if="category.requied" >
                                            <p>{{category.comment}}</p>
                                        </div>
                                    </div>
                                    <div class="accordion-block-icon">
                                        <div class="accordion-icon-manager">
                                            <img src="../assets/icon-edit.svg"/>
                                        </div>
                                        <div class="accordion-icon-manager">
                                            <img src="../assets/icon-delete.svg"/>
                                        </div>
                                        <div class="accordion-icon-manager">
                                            <img src="../assets/icon-reverse.svg"/>
                                        </div>
                                    </div>
                                </div>       
                            </div>
                        </div>
     

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
             doc:"",
             categoryes: [
             {id:1, name:"Обязательные для всех", requied:true, description:"Документы, обязательные для всех сотрудников без исключения",comment:"для всех" },
             {id:2, name:"Обязательные для трудоустройства", requied:true, description:"Документы, без которых невозможно трудоустройство в компании ",comment:"для трудоустройства" },
             {id:3, name:"Специальные", requied:false, description:"",comment:"" },
             {id:0, name:"Остальные", requied:false, description:"",comment:"" }],
             
             documents: [
             {id:0,name:"Паспорт",categoryId:1,used:true},
             {id:1,name:"ИНН",categoryId:1,used:true},
             {id:2,name:"Медицинский полис",categoryId:2,used:true},
             {id:3,name:"Военный билет",categoryId:3,used:true},
             {id:4,name:"Тестовое задание кандидата",categoryId:0,used:false},
             {id:5,name:"Трудовой договор",categoryId:0,used:true},
             {id:6,name:"Медицинская книжка",categoryId:0,used:false}           
             ]

         }
     },
                
              computed: {           
              documents1() {
                  let documents2 = this.documents;
                
                  documents2 = documents2.filter(item => {
                  return item.name.toUpperCase().indexOf(this.doc.toUpperCase())!==-1;
                    })

                 
                    return documents2;
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

.accordion-button::after {
    
    background-image: url(../assets/icon-down-arrow.svg);
    
    
    
}
.accordion-item h2 {
    order: 2;
}
.accordion-button:not(.collapsed)::after {
    background-image: url(../assets/icon-up-arrow.svg);
    
}









.accordion {
    width: 1000px;
}
.accordion-item {
    position: relative;
    margin-bottom: 20px;
}
.accordion-item-input {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
}
.accordion-item-triger {
    display: block;
    padding: 20px;
    border: 1px solid #BFC9E0;
   
}
.accordion-item-content {
    padding: 20px;
    border: 1px solid #BFC9E0;
    border-top: none;
    display: none;

}

.accordion-item-input:checked ~ .accordion-item-content{
    display: block;
}



.accordion-block {
    display: flex;
    justify-content: space-between;
    vertical-align: middle;
}
.accordion-block-text {
    display: flex;
}
.accordion-block-icon {
    display: flex;
}
.accordion-text-h h3{
    font-size: 15px;
    font-weight: 500;
    text-align: left;
   
   
}
.accordion-text-p {
    font-size: 11px;
    font-weight: 400;
}
.accordion-icon-arrow img {
    margin-bottom: 8px;
    margin-right: 10px;
}
.accordion-icon-circle img {
    margin-bottom: 8px;
    margin-left: 10px;
    margin-right: 10px;
}
.accordion-icon-manager img {
    margin-bottom: 8px;
    margin-left: 20px;
}

.accordion-icon-manager img:hover {
    cursor: pointer;
}
.accordion-item-block {
    display: flex;
    justify-content: space-between;
}
.accordion-item-block-text {
    display: flex;
}
.accordion-icon-elipse img {
    margin-left: 20px;
   
    margin-bottom: 10px;
}
.accordion-item-h h4 {
    font-size: 13px;
    font-weight: 400;
}
.accordion-text-pink p {
    font-size: 12px;
    font-weight: 400;
    color: #FF238D;
    margin-left: 20px;
    margin-right: 20px;
}

</style>




  

               

                
            
