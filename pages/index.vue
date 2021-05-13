<template>
  <div class="container">
    <div class="d-flex flex-row justify-content-center">
      <div class="col-md-8 mt-5">
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li
                v-for="(todo, index) in todos"
                :key="index"
                class="list-group-item"
              >
                <a href="" @click.prevent="removeTodo(index)">{{ todo }}</a>
              </li>
            </ul>
            <form @submit.prevent="sub">
              <div class="form-group mt-5">
                <input
                  v-model="todo"
                  type="text"
                  placeholder="Add a Todo"
                  class="form-control"
                />
                <button type="submit" class="btn btn-outline-primary mt-2">
                  Add Todo
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    todos() {
      return this.$store.state.todos
    },
  },
  methods: {
    sub() {
      if (this.todo) {
        this.$store.commit('addTodo', this.todo)
        this.todo = ''
      }
    },
    removeTodo(index) {
      this.$store.commit('removeTodo', index)
    },
  },
}
</script>
