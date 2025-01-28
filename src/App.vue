<template>
  <div class="app">
    <h1>Страница с поставми</h1>
    <div class="app__btns">
      <my-button @click="fetchPosts">Получить посты</my-button>
      <my-button @click="showDialog()">Добавить пост</my-button>
      <my-select v-model="SelectedSort" :options="sortOptions"/>
    </div>
    <my-input v-model="searchQuery" placeholder="Поиск..."/>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"/>
    </my-dialog>
    <post-list :posts="sortedAndSearchedPosts" @remove="removePost"
    v-if="!isPostsLoading"/>
    <div class="" v-else>Идет загрузка...</div>
  </div>
</template>
<script >
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MySelect from "@/components/MySelect.vue";
import axios from "axios";
import MyInput from "@/components/UI/MyInput.vue";
export default {
  components: {MyInput, MyDialog, PostForm, PostList, MySelect},
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      SelectedSort: "",
      sortOptions: [
        {value: "title", name: "По названию"},
        {value: "body", name: "По содержимому"},
      ],
      searchQuery: ""
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
          this.posts = response.data;
          console.log(response);

      }
      catch (e) {
        alert("Ошибка")
      } finally {
        this.isPostsLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPosts();
  },
  computed: {
    sortedPost() {
      return [...this.posts].sort((post1, post2) => post1[this.SelectedSort]?.localeCompare(post2[this.SelectedSort]))
      },
    sortedAndSearchedPosts() {
      return this.sortedPost.filter(post => post.title.includes(this.searchQuery))
    }
  },
  // watch: {
  //   SelectedSort(newValue) {
  //     this.posts.sort((post1, post2) => {
  //       return post1[newValue]?.localeCompare(post2[newValue])
  //     })
  // },}

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
.app__btns {
  margin: 15px 0;
  display: flex;
  justify-content: space-between;
}




</style>