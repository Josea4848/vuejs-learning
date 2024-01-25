<template>
  <div class="form-todo form-group">
      <p>
        <input v-model="name" placeholder="nome" type="text" name="author" class="form-control">
      </p>
      <p>
        <textarea v-model="message" name="message" placeholder="Comentário" class="form-control"></textarea>
      </p>
      <button v-on:click="addData" type="submit" class="btn btn-primary">Comentar</button>
    </div>
</template>

<script>

  export default {
    data() {
      return {
        comments: [],
        name: '',
        message: '',
    }},

    methods: {
      addData() {
        /* if(this.message.trim().length) {
          this.comments.push({name: this.name,message:this.message})
           */

        this.$emit('add-todo', {
          name: this.name,
          message: this.message,
        });

        this.name = '';
        this.message = '';

      }
    }
  }
  
</script>