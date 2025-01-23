<template>
  <div class="app">
    <my-dialog :show="true">
      <post-form @create="createPost"/>
    </my-dialog>
    <post-list :posts="posts" @remove="removePost"/>
  </div>
</template>
<script >
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
export default {
  components: {MyDialog, PostForm, PostList},
  data() {
    return {
      posts:
          [
            {id: 1, title: 'Пост о ГИС', body: 'Описание ГИС'},
            {id: 2, title: 'Пост о ГИС 2', body: 'Описание ГИС 2'},
            {id: 3, title: 'Пост о ГИС 3', body: 'Описание ГИС 3'},
            {id: 4, title: 'Пост о ГИС 4', body: 'Описание ГИС 4'}
          ],
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    }
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


</style>