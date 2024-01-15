<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr>
    <div class="form-todo form-group">
      <p>
        <input v-model="name" placeholder="nome" type="text" name="author" class="form-control">
      </p>
      <p>
        <textarea v-model="message" name="message" placeholder="Comentário" class="form-control"></textarea>
      </p>
      <button v-on:click="addData" type="submit" class="btn btn-primary">Comentar</button>
    </div>
    <hr>

    <div class="list-group">
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
  export default {
      data() {
      return {
        comments: [],
        name:'',
        message:'',
      }
    },
    methods: { 
      addData() {
        if(this.message.trim().length) {
          this.comments.push({name: this.name,message:this.message})
          this.name = '';
          this.message = '';
        }
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

