<template>
  <div id="app">
    

      <post-form
      @add="addPost"
      >
      </post-form>
    <div>
      <h2>Список постов</h2>
      <post-list
        :posts="posts"
      >
      </post-list>

    </div>

  </div>
</template>

<script>
import PostList from '@/components/PostList.vue';
import PostForm from '@/components/PostForm.vue';

export default {
  name: 'App',
  components: {
    PostList,PostForm,
  },
 data(){
    return{
      posts: [
    {
      id:1,
      title: "пост 1",
      body: "text 1"
    },
        {
      id:2,
      title: "пост 2",
      body: "text 2"
    },
  ]
    };
  },
  methods: {
    addPost(post){
      this.posts.push(post);
    },
    deletePost(index){
      this.posts.splice(index, 1)
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 32px;
}
.post{
    border: 2px solid black;
    width: 40%;
    margin: 10px auto;

}
</style>
