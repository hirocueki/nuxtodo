<template>
  <li class="todo-item">
    <div class="todo-item-done">
      <input :checked="done" type="checkbox" @change="onChangeTodo" />
    </div>
    <div class="todo-item-content">
      <div class="todo-item-date">
        {{ new Date(todo.dateTime).toString() }}
      </div>
      <h3 class="todo-item-title">{{ todo.title }}</h3>
      <div v-if="todo.description" class="todo-item-description">
        {{ todo.description }}
      </div>
      <ul v-if="hasCategories" class="todo-item-categories">
        <li
          v-for="category in todo.categories"
          :key="category"
          class="todo-item-category"
        >
          {{ category }}
        </li>
      </ul>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    done: {
      type: Boolean,
      required: true,
    },
  },
  computed: {
    hasCategories() {
      return false
      // return this.todo.categories.length > 0
    },
  },
  methods: {
    onChangeTodo($event) {
      this.$emit('update:done', $event.target.checked)
    },
  },
}
</script>

<style></style>
