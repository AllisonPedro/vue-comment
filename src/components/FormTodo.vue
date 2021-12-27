<template>
    <div class="form-todo form-group">
        <p>
            <input placeholder="Nome" type="text" name="author" class="form-control" v-model="name">
        </p>
        <p>
            <input placeholder="Comentário" type="text" name="message" class="form-control" v-model="message">
        </p>
            <button @click="addComment" type="submit" class="btn btn-primary" > Comentar </button>
    </div>
</template>


<script>
    export default{
        data() {
            return {
                name: "",
                message: "",
            }

        },
        methods:{
            addComment(){
                if(this.message.trim() === ''){
                    return;
                } //if
                
                this.$emit('add-todo', {
                    name: this.name,
                    message: this.message
                })
                this.name = ''
                this.message = ''
                
            },//addComment
        }

    }
</script>