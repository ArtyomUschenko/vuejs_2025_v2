
<template>
  <div class="post">
    <div class="">
      <div class=""><strong>Название поста: </strong> {{post.title}}</div>
      <div class=""><strong>Описание поста: </strong> {{post.body}}</div>
    </div>
    <div class="post__btns">
      <my-button class="btn" @click="deletePost(post)">Удалить</my-button>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      post: {
        type: Object,
        required: true
      }
    },
    methods: {
      deletePost(post) {
        this.$emit("remove", post)
      }
    }

  }
</script>

<style scoped>
.post {
  padding: 15px;
  border: 3px solid #ccc;
  margin-top: 10px;
  margin-right: 10px;
  display: flex;
  align-content: center;
  justify-content: space-between;
}
.btn {
  padding: 5px;
  border-radius: 5px;
  font-size: 10px;
}

</style>