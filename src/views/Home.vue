<template>
  <div class="home">
    <img src="../assets/bg.jpg" alt width="100%" />
    <!-- <template v-slot:extension>
        <v-btn fab color="cyan accent-2" bottom left absolute @click="dialog = !dialog">
          <v-icon>mdi-plus</v-icon>
        </v-btn>
    </template>-->

    <v-container>
      <v-form>
        <v-row>
          <v-col cols="12" sm="6">
            <v-text-field
              label="Enter The Task"
              single-line
              solo
              style="border-radius:30px"
              @keydown.enter="addTodo"
            ></v-text-field>
          </v-col>
        </v-row>
      </v-form>

      <div v-if="todos.length">
        <v-list-item v-for="todo in todos" :key="todo.id">
<!-- 
          <v-btn class="mx-12" outlined small fab color="indigo">
            <v-icon>mdi-pencil</v-icon>
          </v-btn> -->
          <v-list-item-content>
            <v-list-item-title style="text-align:initial">{{todo.text}}</v-list-item-title>
          </v-list-item-content>

          <v-list-item-icon>
            <!-- <v-icon style="color:red">mdi-delete</v-icon> -->
            <v-btn class="ma-2" @click="removeTodo(todo.id)" outlined color="indigo">Done</v-btn>
          </v-list-item-icon>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-container>
  </div>
</template>

<script>
let nextTodoId = 1;

export default {
  name: "Home",
  data() {
    return {
      newTodoText: "",
      todos: [
        {
          id: nextTodoId++,
          text: "Learn Vue"
        },
        {
          id: nextTodoId++,
          text: "Learn about single-file components"
        },
        {
          id: nextTodoId++,
          text: "Fall in love"
        }
      ]
    };
  },
  methods: {
    addTodo() {
      
    },
    removeTodo() {
      
    }
  }
};
</script>