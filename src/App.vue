<template>
  <div class="container py-5">
    <div class="row d-flex justify-content-center align-items-center">
      <div class="col-10">
        <div class="card rounded">
          <div class="card-body p-5">
            <h3 class="mb-3 fw-bold">
              Aktivitas saya sehari hari 
              <span class="badge bg-primary rounded-pill ms-3 fs-6 fw-normal"
                >{{ totalTodo }} task</span
              >
            </h3>

            <form
              @submit.prevent="addTodo"
              class="row align-items-center mb-3 gy-2"
            >
              <div class="col-sm-12 col-md-10">
                <div class="form-floating">
                  <input
                    type="text"
                    class="form-control fs-4"
                    id="floatingInput"
                    placeholder="Todos"
                    autocomplete="off"
                    v-model="todo"
                  />
                  <label for="floatingInput">ISI DISINI</label>
                </div>
              </div>
              <div class="col-sm-12 col-md-2">
                <div class="d-grid">
                  <button
                    type="submit"
                    class="btn btn-primary btn-lg"
                    :disabled="todo.length === 0"
                  >
                    <font-awesome-icon icon="circle-plus" />
                    Tambah
                  </button>
                </div>
              </div>
            </form>

            <List
              :todos="todos"
              @deleteTodo="deleteTodo"
              @doneTodo="doneTodo"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import List from "./components/List.vue";

export default {
  components: { List },
  data() {
    return {
      todo: "",
      todos: [],
    };
  },
  mounted() {
    if (localStorage.getItem("todos") != null) {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
  },
  methods: {
    addTodo() {
      if (this.todo != "") {
        this.todos.unshift({
          activity: this.todo,
          isDone: false,
        });
        this.todo = "";
        this.saveToLocalStorage();
      }
    },
    deleteTodo(indexDelete) {
      this.todos = this.todos.filter((item, index) => {
        if (index != indexDelete) {
          return item;
        }
      });
      this.saveToLocalStorage();
    },
    doneTodo(indexDone) {
      this.todos[indexDone].isDone = !this.todos[indexDone].isDone;
      this.saveToLocalStorage();
    },
    saveToLocalStorage() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
  computed: {
    totalTodo() {
      return this.todos.length;
    },
  },
};
</script>

<style>
@import "./assets/styles.css";
</style>

