<template>
  <div class="w-full h-screen flex justify-center items-center bg-slate-100">
    <div class="shadow-xl p-5 rounded-md">
      <h2 class="text-center text-2xl text-gray-600 mb-4">ToDo List</h2>

      <input
        type="text"
        class="p-2 rounded-md shиadow outline-none min-w[400px]"
        v-model="newTodo"
        @keydown.enter="addNewTodo"
      />

      <button
        class="block w-full py-2 px-5 bg-gray-500 text-white rounded-md mt-2 hover:bg-gray-700"
        @click="addNewTodo"
      >
        Add new todo
      </button>

      <p
        v-if="todoArray.length === 0"
        class="text-xs text-gray-500 text-center mt-2"
      >
        Todo List is empty
      </p>
      
      <!--  -->
      <ul class="mt-5" v-else>
        <!-- list -->
        <li
          class="mt-2 shadow bg-white rounded-md text-xs text-gray-700 py-2 px-4 flex justify-between items-center"
          v-for="(item, idx) in todoArray"
          :key="item"
        >
          <span>{{ item }}</span>
          <button
            class="hover:text-red-500 transition-all"
            @click="removeTodo(idx)"
          >
            <i class="fas fa-trash"></i>
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { mergeProps } from "vue";

export default {
  data() {
    return {
      newTodo: null,
      todoArray: [],
    };
  },

  methods: {
    addNewTodo() {
      if (this.newTodo === null || this.newTodo.trim().length === 0) {
        return;
      }

      this.todoArray.unshift(this.newTodo);
      this.newTodo = null;
    },
    removeTodo(index) {
      this.todoArray.splice(index, 1);
    },
  },
};
</script>
