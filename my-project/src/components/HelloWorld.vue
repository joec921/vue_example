<template>
  <div class="hello">


    <h1>{{ msg }}</h1>




    <div style='display:inline-block;width:100px;' v-for="cat in category" :key="cat.team">
           <div >{{cat.team}}
           <input   v-on:click="showTeam(cat)"
                  type="checkbox"
                   v-model="cat.show"
           class="form-check-input">     
           </div>
    </div> 
<!-- v-on:click="showTeam(cat)" -->
    <div>
      <!-- <label v-on:click="showComplete = !showComplete">

          
                    <input type="checkbox" v-model="showComplete">
                    Show Completed
      </label>    -->
    </div>
    <div  v-for="todo in filteredTodos" :key="todo.name" >

        <div>{{todo.name}} ({{todo.team}})
          <input
                  type="checkbox"
                   v-model="todo.complete"
           class="form-check-input">
          <button v-on:click="deleteItem(todo.name)">delete</button>
        </div>


    </div>


            <!-- Here, a form is used to contain the submit button (which allows keyboard input to be captured.) Notice the v-on directive being used. The .prevent method works the same as submit, but also prevents the default behavior. -->
            <form v-on:submit.prevent="addTodo" class="mt-3">
                <input
                        type="text"
                        v-model="text"
                        class="form-control"
                        placeholder="Add new!">

                <!-- Note the property :disabled. It begins with a colon (:), indicating that Vue should interpret the value as an expression, and not a string.-->
                <button
                        :disabled="submitIsDisabled"
                        class="btn btn-primary mt-2">
                    Add Todo
                </button>
            </form>

  </div>
</template>

<script>

let category = [{
    team:1,
    show: true,
},{
    team:2,
    show: false,
},{
    team: 3,
    show: false,
},{
    team: 4,
    show: false,
}];


let todos = [{
    name:"a",
    complete: true,
    team:1,
    show: true
},{
    name:"b",
    complete: false,
    team:2,
    show: false
},{
    name: "d",
    complete: false,
    team:2,
    show: false
},{
    name: "e",
    complete: false,
    team:1,
    show: true
},{
    name: "f",
    complete: false,
    team:3,
    show: false
},{
    name: "g",
    complete: false,
    team:4,
    show: false
},{
    name: "h",
    complete: false,
    team:3,
    show: false
}];


export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      todos,
      text:'',
      category,
      showComplete:false
    }
  },
  methods:{

    addTodo(){
      todos.push({
          name: this.text,
          complete:false,
          team:4
      })
      this.text= "";
    },

    matchesEl(el) {
        console.log(el)
        return 2;
    },

    deleteItem(name){
        todos.splice(todos.findIndex(i => i.name === name), 1);
    },

    showTeam(cat){
        todos.findIndex(function(value){
           value.team == cat.team ? value.show = !cat.show : 0
        })  
    }


  },
  computed:{
     submitIsDisabled(){
        return this.text==""  ?  true : false
     },
    filteredTodos(){
        //return this.todos
       // return this.todos.filter( i=>i.complete ==true );
        //return this.todos.filter(todo=>this.showComplete ? todo.complete : !todo.complete);
        return this.todos.filter(function(value){           
            return value.show == true ;
        })
    }


  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
