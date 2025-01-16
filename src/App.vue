<template>
  <!-- <Header /> -->
  <div id="app">
   <TodoList /> 
     <!-- <Maincomponent/> -->
      <!-- <Tracker />
      <router-view></router-view> -->
  </div>
</template>

<script>

// import Component from './ASyncComponent/Component.vue';
 import TodoList from'./components/Todolist.vue' ;

 //import Tracker from './Tracker/Tracker.vue';
//import Header from './Tracker/Header.vue';


// import Maincomponent from './ASyncComponent/Maincomponent.vue';
export default{
  components: {
    TodoList
    //Maincomponent
    //Tracker
  }
}
</script>


