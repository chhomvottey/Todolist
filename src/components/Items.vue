<template>
  
        <li :class="{completed: task.completed}">

            <input type="checkbox" v-model="task.completed" @change="$emit('toggleComplete')"/>
            <span v-if="!isEditing">{{ task.text }}</span>
            <input v-else v-model="updatedText" @keyup.enter="saveEdit" @blur="saveEdit" /> &emsp;
            <button class="bg-red-400 p-2 mt-5 text-white" @click="isEditing= !isEditing">{{ isEditing ? 'Save' :'Edit' }}</button> &emsp;
            <button class="bg-pink-400 p-2 mt-5 text-white" @click="$emit('deleteTask')">Delete</button>
        </li>
    
</template>
<script>


export default{
    props:{
        task: Object
    },
    data(){
        return{
            isEditing: false,
            updatedText: this.task.text
        };
    },

    methods:{
        saveEdit(){
            if(this.updatedText.trim()){
                this.isEditing = false;
                this.$emit('updateTask',this.updatedText);
            }
        }
    },

    watch:{
        task:{
            handler(newTask){
                if(!this.isEditing){
                    this.updatedText = newTask.text;
      
                }
            },
            deep: true
        }

    }
};
</script>
<style>
.completed{
    text-decoration: line-through;
    color: grey;
}
</style>