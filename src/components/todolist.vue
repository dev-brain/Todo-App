<template>
  <div>
    <div class="default-input" style=" margin: auto;
  width: 100%;
  padding: 20px;">
      <vs-input
        size="large"
        class="inputx"
        placeholder="What needs to be done"
        v-model="newTodo"
        style="width:100%"
        @keyup.enter="addtodo"
      />
    </div>

    <div style="margin:20px">
      <vs-row>
        <vs-checkbox
          @change="checkAllTodos"
          :checked="!anyRemaining"
          style="font-size:12px;margin-bottom:10px"
        >Select All</vs-checkbox>

        <p style="margin:0 0 0 auto;font-size:15px">{{remaining}} Items left</p>
      </vs-row>
      <div class="animate__animated animate__fadeIn">
        <div v-for="(todo,index) in todos" :key="todo.id">
          <vs-row style="width:100%;margin:10px 0 10px 0">
            <vs-checkbox v-model="todo.completed" />

            <p
              v-if="!todo.editing"
              @click="editTodo(todo)"
              :class="{completed:todo.completed}"
              style="text-align:left;width:75%;font-size:20px;margin-left:20px;font-weight:100;"
            >{{todo.title}}</p>
            <!-- <vs-input v-else type="text" v-model="todo.title" id="lol" /> -->
            <input
              v-else
              type="text"
              v-model="todo.title"
              id="lol"
              @blur="doneEdit(todo)"
              @keyup.enter="doneEdit(todo)"
              @keyup.esc="cancelEdit(todo)"
              v-focus
            />
            <vs-icon
              icon="delete"
              size="small"
              color="red"
              style="margin-left:auto"
              @click="removeTodo(index)"
            ></vs-icon>
          </vs-row>
          <vs-divider position="center"></vs-divider>
        </div>
      </div>
      <!-- <vs-list>
        <vs-row style="margin:10px 0px 0px 20px;width:90%">
          <vs-list-item
            v-if="!todo.editing"
            class="centerx"
            
            style="border-bottom:1px solid transparent; width:100%;text-align:initial"
          >

          </vs-list-item>
        </vs-row>
      </vs-list>-->
    </div>
  </div>
</template>

<script>
export default {
  name: "todo-list",
  data() {
    return {
      newTodo: "",
      beforeEditTitle: "",
      idForTodo: 3,
      todos: [
        {
          id: 1,
          title: "finish Vue ",
          completed: false,
          editing: false
        },
        {
          id: 2,
          title: "Take over",
          completed: false,
          editing: false
        },
        {
          id: 3,
          title: "finish Vue",
          completed: false,
          editing: false
        }
      ]
    };
  },
  directives: {
    focus: {
      // directive definition
      inserted: function(el) {
        el.focus();
      }
    }
  },
  methods: {
    addtodo() {
      if (this.newTodo.trim().length == 0) {
        return;
      }

      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false
      });
      (this.newTodo = ""), this.idForTodo++;
    },

    editTodo(todo) {
      // alert("lol");
      this.beforeEditTitle = todo.title;
      todo.editing = true;
    },
    doneEdit(todo) {
      if (todo.title.trim().length == 0) {
        todo.title = this.beforeEditTitle;
      }
      todo.editing = false;
    },
    cancelEdit(todo) {
      todo.title = this.beforeEditTitle;
      todo.editing = false;
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    checkAllTodos() {
      this.todos.forEach(todo => (todo.completed = event.target.checked));
    }
  },
  computed: {
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    },
    anyRemaining() {
      return this.remaining != 0;
    }
  }
};
</script>
 
<style scoped>
@import url("https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.0.0/animate.min.css");
#lol {
  padding: 15px;
  width: 80%;
  margin-left: 20px;
  font-size: large !important;
  border: 1px solid #ccc;
  font-weight: 100 !important;
}

.completed {
  text-decoration: line-through;
}
</style>
