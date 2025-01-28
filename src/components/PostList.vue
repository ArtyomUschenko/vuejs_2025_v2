
<template>
  <div class="" v-show="posts.length > 0">
    <h3>Список пользователей</h3>
    <transition-group name="post-list">
      <post-item v-for="post in posts"
                                  :post="post"
                                  :key="post.id"
                                  @remove="$emit('remove', post)"
    /></transition-group>

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
.post-list-enter-active,
.post-list-leave-active {
  transition: all 0.3s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.post-list-move, /* apply transition to moving elements */
.post-list-enter-active,
.post-list-leave-active {
  transition: all 0.5s ease;
}

.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

/* ensure leaving items are taken out of layout flow so that moving
   animations can be calculated correctly. */
.post-list-leave-active {
  position: absolute;
}
</style>