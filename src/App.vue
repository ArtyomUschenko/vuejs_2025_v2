
<template>
  <div class="app">
    <form @submit.prevent>
      <h4>Создание поста</h4>
      <input class="input" type="text" placeholder="Название" v-bind:value="title" @input="title = $event.target.value">
      <input class="input" type="text" placeholder="Описание" v-bind:value="body" @input="body = $event.target.value">
      <button class="btn" @click="createPost()">Создать</button>
    </form>
    <div class="post" v-for="post in posts">
      <div class=""><strong>Название поста: </strong> {{post.title}}</div>
      <div class=""><strong>Описание поста: </strong> {{post.body}}</div>
    </div>
  </div>
</template>

<script >
  export default {
    data() {
      return {
        posts:
            [
              {id: 1, title: 'Пост о ГИС', body: 'Описание ГИС'},
              {id: 2, title: 'Пост о ГИС 2', body: 'Описание ГИС 2'},
              {id: 3, title: 'Пост о ГИС 3', body: 'Описание ГИС 3'},
              {id: 3, title: 'Пост о ГИС 4', body: 'Описание ГИС 4'}
            ],
        title: "",
        body: "",
      }
    },
    methods: {
      createPost() {
        const newPost = {
          id: Date.now(),
          title: this.title,
          body: this.body
        }
        this.posts.push(newPost)
        this.title = "";
        this.body = "";
      },
    }
  }
</script>


<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app {
    padding: 20px;
  }
  .post {
    padding: 15px;
    border: 3px solid #ccc;
    margin-top: 10px;
    margin-right: 10px;
  }
  .input {
    margin-top: 10px;
    display: block;
    width: 50%;
    padding: 10px;
    border: 3px solid #ccc;
    border-radius: 5px;
    font-size: 20px;
  }
  h4 {
    margin: 15px;
    font-size: 40px;
  }
 .btn {
    padding: 10px;
    border: 3px solid #ccc;
    margin-top: 10px;
    border-radius: 5px;
    font-size: 20px;
    background-color: #ccc;
    color: #fff;
    cursor: pointer;
  }
</style>