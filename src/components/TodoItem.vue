<template>
    <li>
        <label><input type="checkbox" v-model="todo.isComplete" /></label>
        <span>&nbsp;</span>
        <del v-if="todo.isComplete">{{todo.name}}</del>
        <span v-else>{{todo.name}}</span>
        <span>&nbsp;</span>
        <button type="button" v-on:click="$emit( 'remove-todo', todo.id )">X</button>
      </li>
</template>
<script>
export default {
  name: 'TodoItem',
  props: {
    todo: Object
  }
}
</script>