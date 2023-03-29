<template>
    <div>
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
            содержание поста:{{post.body}}
        </div>
        <button
        
        @click="deletePost(index)">удалить</button>
        </div>
    </div>

</template>

<script>
export default {
    
    name:'PostList',
    props: {
        posts: {
            type: Array,
            default() {
                return []
            },
            required: false,
        },
    },
methods:{
    deletePost(index){
        this.$emit('delete-Post', index)
    }
},
}
</script>

<style>

</style>