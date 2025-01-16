<template>
    <div class="todo-list  bg-sky-300 app mt-5 p-4">
        <h1 style="font-size: 2rem; " class="text-center">TodoList</h1>
        <div class="mt-5">
            <input class="p-2" v-model="newTask" @keyup.enter="addTask" type="text" placeholder="Enter Add..."> &emsp;
            <button class="bg-teal-400 p-2  text-white" @click="addTask">Add Task</button>  
        </div>
        
           
          
                
            
            
       

        <div class="mt-4 Result-Todolist">
            <ul>
                <Items 
                v-for="(task,index) in tasks" 
                :key="index"
                :task="task"
                @deleteTask="deleteTask(index)"
                @toggleCompleted="toggleCompleted(index)"
                @updateTask="updateTasks(index,$event)"

                
                />
                
            </ul>
        </div>
    </div>

</template>

<script>
import Items from './Items.vue';
export default{
    components:{
        Items},

    
    data(){
        return{
            newTask:'',
            tasks:[]
        };
    },
    created(){
        const storedTasks = localStorage.getItem('tasks');
        if(storedTasks){
            this.tasks = JSON.parse(storedTasks);
        }
    },
    watch:{
        tasks:{

            handler(updateTasks){
            localStorage.setItem('tasks',JSON.stringify(updateTasks));
        },
        deep:true

        }
       
       
    },
    methods: {
        addTask(){
            if(this.newTask.trim()){
                this.tasks.push({text: this.newTask,completed:false});
                this.newTask='';
            }
        },
        deleteTask(index){
        this.tasks.splice(index, 1);
    },
    updateTasks(index,updateText){
    this.tasks[index].text= updateText;
    },
    toggleCompleted(){
            this.tasks[index].completed = !this.tasks[index].completed;
        }
       
    }
   
    

};

</script>
<style>
.app{
    width: 50%;
    margin: auto;
    border-radius: 10px;
    margin-top: 10%;
}
.input{
    width: 80%;
    height: 40px;
    border-radius: 20px;
    padding: 10px;
}
</style>