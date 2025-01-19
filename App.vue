<template>
  <div>
  <div id="app">
<h1 class="title">{{title}}</h1>
<div class="todo">
<input v-model="todo" type="text" placeholder="New Task"/>
<button @click="addTodo(id++)">+</button>
 <hr/>  

<p>{{todo}}</p>
<todo-list :todos='todos' @removeTodo= 'removeTodo'/>

<todo-total :todos='todos' :title='TitleTodoLength'/>





</div>

<hr/> 

</div>

  </div>
</template>
<script>



import todoList from './components/todoList.vue'
import todoTotal from './components/todoTotal.vue'
export default {
  components:{
    todoList,
    todoTotal
  },

  data() {
    return {
       TitleTodoLength:'Tasks:',
       title: "Todo list",
       todo:"",
       todos: [],
       isDone:false,
       id:0
      };
},
async mounted(){
  const data = await localStorage.getItem('todos')
  data ? this.todos=JSON.parse(data):null
},



methods: {
addTodo(){

      if(this.todo !=''){
        this.todos.push({
          id:this.id,
          text:this.todo,
          isComplete:this.isDone,})

          localStorage.setItem('todos', JSON.stringify(this.todos)) }
        this.todo="";
      },
    removeTodo(index){
    console.log(index);
    this.todos.splice(index,1);
    localStorage.setItem('todos', JSON.stringify(this.todos))
  }

    },
  }
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  background-color: #292832;
 padding-top: 30px;
 margin-bottom:40px;
   width: 100%;
  height: 100vh;
  padding-right:19px;
   margin: 0 auto;
}

.todo{

  width: 100%;
  height: 470px;
  border:1px solid #fff;
  background:#292832;
  border-radius:38px;
  padding:30px;
 outline: 1px solid #fafafa;
 border-radius: 5px;
 min-height:500px;
 text-align: left;
 margin: 0 auto;
 margin-right:0;

 

 &__id{
  color:#2c3e50;
  font-weight:bold;
  
 }
 &__text{
  font-size:15px;
  color:#FFF;
  text-transform: capitalize;
  bottom: 25px;
  font-weight: 100;
 
  

  &_isShow{
  color:#ccc;
  text-decoration: line-through;

 }
 }
 &__check{
  display:inline-block;
  font-size: 18px;
  margin-right:5px;
  width: 10px;
    height: 10px;
    border-radius: 50%;


 }

}
input{

  text-align: left;
  font-size: 16px;
  border-radius:18px;
  padding:10px 10px;
  border-color:#a8b3bd;
  border:7px;


}

input:focus{
border: 1px solid rgb(252, 252, 255);
box-shadow: 1px 1px 2px 0 rgb(242, 242, 245);
}


button{
  color: #FFF;
  background-color: #7459ef;
  border: #7459ef;
  font-size: 22px;
  font-weight: 100;
  width:43px;
  height:43px;
    border-radius: 50%;
    padding:0px 0px;
 
}
hr{
  margin-left: auto;
  margin-right: auto;
}

@media (min-width:310px){
  #app{
    padding-right:19px;
    width: 100%;
    height: 100vh;
  }
  .todo{
    width:100%;
    height: 100%;
    padding: 10px 10px;}

    button{
    font-size:10px;
    position:absolute;
    top:165px;
    left:290px;
    width:25px;
    height:25px;
    padding:0px 0px;
  }
  input{
  font-size:14px;
  width: 285px;

  }
}

@media (min-width:350px){
  button{
    font-size:15px;
    position:absolute;
    top:165px;
    left:350px;
    width:25px;
    height:25px;
    padding:0px 0px;
  }
  input{
  font-size:14px;
  width: 342px;

  }
}


@media (min-width:400px){

  .todo{
    width:100%;
    height: 100%;
    padding: 10px 10px;
  
  &__text {
    font-size: 30px;
  
  }
  &__check{
  display:inline-block;
  font-size: 30px;
  margin-right:5px;


 }
}
  input{
  font-size:14px;
  width: 385px;

  }
  button{
   
    font-size:10px;
    position:absolute;
    top:165px;
    left:389px;
    width:27px;
    height:27px;
    padding:0px 0px;
  

  }
  p{
    font-size:30px;
  }
}
@media (min-width:760px){

  button{
    font-size:30px;
    position: absolute;
    left:710px;
    top:165px;
    width:40px;
    height:40px;
    padding:0px 0px;
  }
  input{
  font-size:30px;
  width: 720px;
  }
  p{
    font-size:30px;
  }

  input[type=checkbox]{
    width:20px;
    height: 20px;
  }

}
@media (min-width:1000px){
  button{
    font-size:30px;
    position: absolute;
    left:960px;
    top:165px;
    width:45px;
    height:45px;
    padding:0px 0px;
  }
  input{
  font-size:30px;
  width: 975px;
  

  }
  p{
    font-size:30px;
  }
  input[type=checkbox]{
    width:25px;
    height: 25px;
  }
}
@media (min-width:1144px){
  input{
  font-size:40px;
  width: 1300px;
  }
  button{
    font-size:42px;
    position:absolute;
    left:1270px;
    top:168px;
  }
}
@media (min-width:1400px){
  .todo{
    width:100%;
    height: 100%;
    padding: 10px 10px;
  
  &__text {
    font-size: 40px;
  
  }
  &__check{
  display:inline-block;
  font-size: 90px;
  margin-right:5px;


 }

}
  input{
  font-size:40px;
  width: 1380px;

  }
  button{
    font-size:42px;
    position:absolute;
    left:1360px;
    top:168px;
  }
  p{
    font-size:40px;
  }
  input[type=checkbox]{
    width:27px;
    height: 27px;
  }
}
@media (min-width:2500px){
  input{
  font-size:40px;
  width: 2490px;

  }
  button{
    font-size:44px;
    position:absolute;
    left:2460px;
    top:168px;
  }
}


</style>
