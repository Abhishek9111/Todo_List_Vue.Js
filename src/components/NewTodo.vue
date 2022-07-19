<template>
    <form @submit.prevent="addTodo()" action="" class="col-12 lf-6">
        <input v-model="newTodo" placeholder="Enter the new Todo" type="text" class="form-control" />
    </form>
</template>

<script>
export default {
    data(){
        return{
            newTodo:""
        }
    },
    methods: {
        addTodo(){
            if(this.newTodo.length>1){
                this.$emit('on-addTodo',this.newTodo)
            }
            this.newTodo=''
        }
    }
}
</script>


<style scoped>

</style>