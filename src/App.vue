<template>
  <div id="app">
    <div>
      <h1>Создание поста</h1>
    </div>

    <div>
      <input
        v-model="title"
        type="text"
       placeholder="название поста"
       >
    </div>

    <div>
      <input
      v-model="text"
      type="text"
       placeholder="список поста">
    </div>
    
    <div>
      <button @click="addPost">выложить пост</button>
    </div>


    <div>
      <h2>Список постов</h2>
    </div>
    <div
    v-if="posts.length === 0"
    >
      добавленых постов нет
    </div>

    <div
      v-for="(post, index) in posts"
      :key="index"
      class = "post"
      >
      <div>
        Название поста: {{post.title}}
      </div>
      <div>
        содержание поста:{{post.text}}
      </div>
      <button
       
       @click="deletePost(index)">удалить</button>
    </div>
    </div>
    
    
    <!-- <div>
    количество: {{ likes }}
    </div>
    
    <div>
    количество дизлайков: {{ dislikes }}
    </div> -->
    <!-- <div>
    <button class="like" @click=addlike>лайк</button>
    <button class="dizlike" @click=adddislike>дизлайк</button>
    </div> -->
  
</template>

<script>


export default {
  name: 'App',
 data(){
    return{
      title: "",
      text: "",
      // likes: 0,
      // dislikes: 0,
      posts: [
    {
      id:1,
      title: "пост 1",
      text: "text 1"
    },
        {
      id:2,
      title: "пост 2",
      text: "text 2"
    },
  ]
    };
  },
  methods: {
    // addlike(){
    // this.likes += 1
    // },
    // adddislike(){
    //   this.dislikes += 1
    // },
    addPost(){
      this.posts.push({
        title: this.title,
        text: this.text,
      });
      this.title = this.text ="";
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
/* .like{
  background: green;
  color: white;
  cursor: pointer;
}
.dizlike{
  background: red;
  color: white;
  cursor: pointer;

} */
</style>
