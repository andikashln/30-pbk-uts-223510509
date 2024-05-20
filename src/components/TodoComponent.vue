<template>
    <div>
      <!-- Todo Form -->
      <form @submit.prevent="submitTodo" class="row align-items-center mb-3 gy-2">
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
            <label for="floatingInput">Apa rencana kegiatanmu hari ini?</label>
          </div>
        </div>
        <div class="col-sm-12 col-md-2">
          <div class="d-grid">
            <button type="submit" class="btn btn-primary btn-lg" :disabled="todo.length === 0">
              <font-awesome-icon icon="circle-plus" />
              Daftar Rencana Hari Ini
            </button>
          </div>
        </div>
      </form>
  
      <!-- Todo List -->
      <ul class="list-group list-group-flush">
        <li
          v-for="(todo, index) in todos"
          :key="index"
          class="list-group-item"
        >
          <div class="row gy-2">
            <div
              class="col-sm-12 col-md-auto me-auto align-self-center fs-5"
              :class="{ 'text-decoration-line-through text-muted': todo.isDone }"
              v-if="editedTodoIndex !== index"
            >
              {{ todo.activity }}
            </div>
            <div class="col-sm-12 col-md-auto" v-else>
              <input
                v-model="editedTodoText"
                class="form-control"
                @keyup.enter="saveEdit(index)"
                @keyup.escape="cancelEdit"
              />
            </div>
            <div class="col-sm-12 col-md-auto">
              <div class="row gx-2">
                <div class="col-auto">
                  <button
                    class="btn"
                    :class="[
                      todo.isDone ? 'btn-outline-secondary' : 'btn-outline-success',
                    ]"
                    @click="doneTodo(index)"
                  >
                    <font-awesome-icon icon="circle-check" />
                  </button>
                </div>
                <div class="col-auto">
                  <button
                    class="btn"
                    :class="[
                      todo.isDone ? 'btn-outline-secondary' : 'btn-outline-danger',
                    ]"
                    @click="deleteTodo(index)"
                  >
                    <font-awesome-icon icon="eraser" />
                  </button>
                </div>
                <div class="col-auto">
                  <button
                    class="btn btn-outline-primary"
                    v-if="editedTodoIndex !== index"
                    @click="editTodo(index, todo.activity)"
                  >
                    <font-awesome-icon icon="edit" />
                  </button>
                  <button
                    class="btn btn-outline-secondary"
                    v-else
                    @click="cancelEdit"
                  >
                    <font-awesome-icon icon="times" />
                  </button>
                  <button
                    class="btn btn-outline-secondary"
                    v-if="editedTodoIndex === index"
                    @click="saveEdit(index)"
                  >
                    <font-awesome-icon icon="check" />
                  </button>
                </div>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      todos: Array,
    },
    data() {
      return {
        todo: "",
        editedTodoIndex: null,
        editedTodoText: "",
      };
    },
    methods: {
      submitTodo() {
        if (this.todo.trim() !== "") {
          this.$emit('add-todo', this.todo);
          this.todo = "";
        }
      },
      deleteTodo(index) {
        this.$emit('delete-todo', index);
      },
      doneTodo(index) {
        this.$emit('done-todo', index);
      },
      editTodo(index, text) {
        this.editedTodoIndex = index;
        this.editedTodoText = text;
      },
      cancelEdit() {
        this.editedTodoIndex = null;
        this.editedTodoText = "";
      },
      saveEdit(index) {
        if (this.editedTodoText.trim() !== "") {
          this.$emit('save-edit', { index, text: this.editedTodoText });
          this.cancelEdit();
        }
      },
    },
  };
  </script>
  