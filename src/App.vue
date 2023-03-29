<template>
  <div id="app">
    

      <post-form
      @add="addPost"
      >
      </post-form>
    <div>

      <h2>Список постов</h2>
      <input 
        v-model="searchString"
        placeholder="поиск поста" 
        
      >
      <post-list
        :posts="searchedPost"
        @delete-Post="deletePost"
      >
      </post-list>

    </div>

  </div>
</template>

<script>
import PostList from '@/components/PostList.vue';
import PostForm from '@/components/PostForm.vue';
import axios from 'axios'

export default {
  name: 'App',
  components: {
    PostList,PostForm,
  },
 data(){
    return{
      title: '',
      body: '',
      posts: [],
      searchString: '',
    };
  },
  computed: {
    searchedPost(){
      const sortedPost = [];
      for (const post of this.posts){
        if (post.title.includes(this.searchString)){
          sortedPost.push(post);
        }
      }
      return sortedPost;
    },
  },
  methods: {
    addPost(post){
      this.posts.push({
        ...post,
        
      });
    },
    deletePost(index){
      this.posts.splice(index, 1)
    },
    async getPosts() {
      const url = 'https://jsonplaceholder.typicode.com/posts'
      try {
        const response = await axios.get(url)
        this.posts = response.data
      }
      catch(error) {
        console.error('ОШИБКА')
        console.error('произошла ошибка при получении постов')
      }
    },
  },
 async created(){
    await this.getPosts()
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin-top: 60px;
  font-size: 32px;
}

.post{
    border: 2px solid black;
    width: 40%;
    margin: 10px auto;

}
</style>
