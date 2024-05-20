<template>
  <div class="wrapper">
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <!-- ... -->
    </nav>

    <div class="container py-5">
      <div class="row d-flex justify-content-center align-items-center">
        <div class="col-10">
          <div class="card rounded">
            <div class="card-body p-5">
              <!-- Title and total tasks -->
              <h3 class="mb-3 fw-bold">
                To-Do List
                <span class="badge bg-primary rounded-pill ms-3 fs-6 fw-normal">{{ totalTodo }} task</span>
              </h3>

              <!-- Todo Component -->
              <TodoComponent
                :todos="todos"
                @add-todo="addTodo"
                @delete-todo="deleteTodo"
                @done-todo="doneTodo"
                @save-edit="saveEdit"
              />

              <!-- User and Post Component -->
              <UserPostComponent
                :users="users"
                :posts="posts"
                @select-user="fetchPosts"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoComponent from './components/TodoComponent.vue';
import UserPostComponent from './components/UserPostComponent.vue';

export default {
  components: {
    TodoComponent,
    UserPostComponent,
  },
  data() {
    return {
      todos: [],
      posts: [],
      users: [],
    };
  },
  mounted() {
    if (localStorage.getItem("todos") !== null) {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
    this.fetchUsers();
  },
  methods: {
    addTodo(todo) {
      if (todo.trim() !== "") {
        this.todos.unshift({
          activity: todo,
          isDone: false,
        });
        this.saveToLocalStorage();
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
      this.saveToLocalStorage();
    },
    doneTodo(index) {
      this.todos[index].isDone = !this.todos[index].isDone;
      this.saveToLocalStorage();
    },
    saveEdit({ index, text }) {
      if (text.trim() !== "") {
        this.todos[index].activity = text;
        this.saveToLocalStorage();
      }
    },
    saveToLocalStorage() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    async fetchUsers() {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        const data = await response.json();
        this.users = data;
      } catch (error) {
        console.error('Error fetching users:', error);
      }
    },
    async fetchPosts(userId) {
      if (!userId) return;
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${userId}`);
        const data = await response.json();
        this.posts = data;
      } catch (error) {
        console.error('Error fetching posts:', error);
      }
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
``
