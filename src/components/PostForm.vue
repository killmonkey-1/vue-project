<template>
  <div>
        <div>
            <h1>Создание поста</h1>
        </div>

        <div>
            <input
                v-model="post.title"
                type="text"
            placeholder="название поста"
            >
        </div>

        <div>
            <input
            v-model="post.body"
            type="text"
            placeholder="список поста">
        </div>
            
        <div>
            <button @click="addPost">выложить пост</button>
        </div>
  </div>
</template>

<script>
export default {
    name:'PostForm',
    data(){
        return{
            post:{
                title: '',
                body: '',
            },
        }
    },
    methods:{
        addPost(){
            this.$emit('add',this.post)
            this.$emit('clear')
        },
    },
}
</script>

<style>

</style>