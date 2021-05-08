<template>
  <div class="nav-container">
    <ul>
      <li
        class="todo-item"
        :class="{ 'todo-item--active': filterState == 'all' }"
        @click="updateFilter('all')"
      >
        All
      </li>
      <li
        class="todo-item"
        :class="{ 'todo-item--active': filterState == 'active' }"
        @click="updateFilter('active')"
      >
        Active
      </li>
      <li
        class="todo-item"
        :class="{ 'todo-item--active': filterState == 'completed' }"
        @click="updateFilter('completed')"
      >
        Completed
      </li>
    </ul>
    <hr />
  </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
  name: "nav-filters",
  data() {
    return {
      filterState: "all",
    };
  },
  methods: {
    updateFilter(newState) {
      this.filterState = newState;
      eventBus.$emit("filterChanged", this.filterState);
    },
  },
};
</script>

<style lang="scss" scoped>
$border-color: #bdbdbd;
$primary-color: #2f80ed;

.nav-container {
  ul {
    display: flex;
    justify-content: space-around;
  }
  .todo-item {
    font-family: "Raleway";
    font-weight: 600;
    font-size: 14px;
    list-style: none;
    padding: 15px 0px;
    min-width: 90px;
    text-transform: capitalize;

    &--active {
      border-bottom: 4px solid $primary-color;
    }
  }
}
</style>