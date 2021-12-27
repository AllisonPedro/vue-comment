<template>
    <div class="container">
            <h1>Comentarios</h1>
            <hr>
            <FormTodo v-on:add-todo="addComment"/>
            <hr>
            <div class="list-group">
            <p v-if="comments.length <= 0">Sem Comentarios...</p>
                <div class="list-group-item" v-for="com, index in allComments" :key="index">
                    <span class="comment__autor">Autor: <strong>{{com.name}}</strong></span>
                    <p>{{com.message}}</p>
                    <div>
                        <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                    </div>
                </div>
            </div>
            <hr>
    </div>
</template>

<script>
import FormTodo from "./FormTodo.vue"
export default{
    components:{
        FormTodo
    },
    
        data(){
            return{
                comments:[]//comments
                
            } //return 
        }, //data()
        methods: {
            addComment(comment){
                this.comments.push(comment)
            },

            removeComment(index){
                this.comments.splice(index, 1)
            }//removeComment
        },//methods

        computed:{
            allComments(){
                return this.comments.map(comment => ({
                    ...comment,
                    name: comment.name.trim() === '' ? 'Anônimo' : comment.name
                }))//return
            }//allComments
        }//computed


}

    

</script>


 
     