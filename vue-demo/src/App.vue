<template>
  <div id="app">
    <input v-model="message">
    <input :value="message" @input="handleChange">
    {{ message }} {{ message + message }}
    <div :id="message"></div>
    <todo-list>
      <todo-item @delete="handleDelete" v-for="item in list" :key="item.title" :title="item.title" :del="item.del">
        <template v-slot:pre-icon="{ value }">
          <span>前置图标{{ value }}</span>
        </template>
      </todo-item>
    </todo-list>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  components: {
    TodoItem,
    TodoList
  },
  data() {
    return {
      message: 'hello world',
      list: [{
        title: '课程1',
        del: false
      }, {
        title: '课程2',
        del: true
      }],
    }
  },

  methods: {
    handleChange(e) {
      this.message = e.target.value
    },
    handleDelete(val) {
      // eslint-disable-next-line no-console
      console.log('handleDelete', val)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
