<template>
  <div id="app">
    <div class="container">
      <h1 class="page-title">#todo</h1>
      <nav-filters></nav-filters>
      <new-todo-bar v-if="filter != 'completed'"></new-todo-bar>
      <todo-list></todo-list>
      <footer>
        <p>created by matuzapata - devChallenges.io</p>
      </footer>
    </div>
  </div>
</template>

<script>
import NavFilters from "@/components/NavFilters";
import NewTodoBar from '@/components/NewTodoBar'
import TodoList from '@/components/TodoList'
import {eventBus} from '@/main'

export default {
  name: "App",
  components: {
    NavFilters,
    NewTodoBar,
    TodoList,
  },
  data() {
    return {
      filter: 'all'
    }
  },
  created() {
    eventBus.$on('filterChanged', (newFilter) => this.filter = newFilter)
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@700;600;500&display=swap");


* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  justify-content: center;
  margin-top: 30px;
  font-family: "Raleway";

  .container {
    width: 600px;
    text-align: center;
    display: grid;
    grid-row-gap: 10px;
  }
}

.page-title {
  font-weight: 700;
  font-size: 36px;
}

footer {
  margin-top: 300px;
  padding: 20px;
  p {
    color: #A9A9A9;
  }
}
</style>
