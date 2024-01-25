<template>
  <div class="container">
    <h1>Seu celular foi invadido</h1>
    <hr>
    <FormTodo v-on:add-todo="addComment"></FormTodo>
    <hr>

    <div class="list-group">
      <p v-if="!comments.length">Sem comentários</p> 
      <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="comment">
        <span class="comment__autor">Autor: {{comment.name}}</span>
        <p>{{comment.message}}</p>
        <div>
          <a v-on:click.prevent="removeData(index)"  href="#" title="Excluir">Excluir</a>
        </div>
      </div>     
    </div>

  </div>     
</template>

<script>
  import FormTodo from "./FormTodo";

  export default {
      components: {
        FormTodo
      },

      data() {
        return {
          comments: []
        }
  },
    methods: {
      addComment(comment) {
        this.comments.push(comment);
      },
      
      removeData(index) {
        this.comments.splice(index,1);
      }
    },

    computed: {
      allComments() {
        return this.comments.map(comment => {
          return {...comment, name: comment.name.trim() === '' ? 'Anônimo' : comment.name};
        })
      }
    },
    watch: {
      comments() {
        alert("ahha");
      }
    }
  }
</script>

