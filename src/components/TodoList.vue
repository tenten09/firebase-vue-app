<template>
  <div>
    <b-container>
      <b-card
        title="TODO"
        img-src="https://picsum.photos/600/300/?image=25"
        img-alt="Image"
        img-top
        tag="article"
        style="height: 20;"
        class="mb-2" 
        img-height="240"
     >
        <v-list two-line>

            <b-row :key="index" v-for="(todo, index) in todos.slice(0, 6)" class="mt-2">
              <b-col cols="8" :class="[{line: todo.complete}, 'text-left']">
                <h5>{{todo.text}}</h5>
                <h5>{{todo.type}}</h5>
              </b-col>
              <b-col cols="4" class="text-right">
                <b-button 
                  @click="handleCompleteTodo(index)" 
                  :variant="todo.complete ? '' : 'primary'">
                  {{todo.complete ? '完了' : '未完了'}}
                </b-button>
                <b-button @click="handleDeleteTodo(index)" variant="danger">delete</b-button>
              </b-col>
            </b-row>
        </v-list>
      </b-card>
    </b-container>
  </div>
</template>


<script>
  export default {
    name: 'TodoList',
    props: ['todos'],
    methods: {
      handleDeleteTodo(index) {
        this.$emit("handleParentDeleteTodo", index);
      },
      handleCompleteTodo(index) {
        this.$emit('handleParentCompleteTodo', index);
      }
    },
  }
</script>

<style scoped>
  .line {
    text-decoration: line-through;
  }
</style>