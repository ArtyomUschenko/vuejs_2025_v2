
<template>
  <div class="" v-show="posts.length > 0">
    <h3>Список пользователей</h3>
    <post-item v-for="post in posts"
    :post="post"
    :key="post.id"
               @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-show="posts.length <= 0" style="color: red; margin-top: 10px">Список постов пуст</h2>
</template>

<script>
 import PostItem from "@/components/PostItem.vue";

 export default {
   components: {PostItem},
    props: {
      posts: {
        type: Array,
        required: true
      }
    }
 }
</script>




<style scoped>
h3 {
  margin-top: 30px;
}
</style>