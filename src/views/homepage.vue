<template>
    
    <button @click="addPost">Add Post</button>
    <h2>All</h2>
    <ul>
        <single-post 
            v-for="post in posts" 
            :post="post" 
            :key="post.id"
            @deleteUsingEmit = "deleteThis"
            @fav = 'addFav'
        />
    </ul>
    <h2>Fav</h2>
    <ul>
        <single-post 
            v-for="post in favs" 
            :post="post" 
            :key="post.id"
            @deleteUsingEmit = "deleteThis"
            @fav = 'addFav'
        />
    </ul>
    <h2>UnFav</h2>
    <ul>
        <single-post 
            v-for="post in unFavs" 
            :post="post" 
            :key="post.id"
            @deleteUsingEmit = "deleteThis"
            @fav = 'addFav'
        />
    </ul>

</template>

<script>
import number from "@/components/number.vue";
import SinglePost from "../components/SinglePost.vue";

    export default {
        name: 'homepage',
        components: {SinglePost, number},
        data(){
            return {
                message: 'Hello Bangladesh',
                posts: [
                {
                    id: 1,
                    title: 'Post 1',
                    fav: true
                },
                {
                    id: 2,
                    title: 'Post 2',
                    fav: false
                },
                {
                    id: 3,
                    title: 'Post 3',
                    fav: true
                }
                ]
            }
        },
        computed: {
            favs(){
                return this.posts.filter(post => post.fav)
            },
            unFavs(){
                return this.posts.filter(post => !post.fav)
            }
        },
        methods: {
            deleteThis($post){
            this.posts = this.posts.filter(pos => pos.id !== $post.id)
        },
        addPost(){
            this.posts.push({
                id: this.posts.length + 1,
                title: `Post ${this.posts.length + 1}`
            })
        },
        addFav(post){
            this.posts = this.posts.map(pos => {
                if (pos.id === post.id){
                    pos.fav = !pos.fav
                }
                return pos
            })
        }
        }
    }
</script>

<style scoped>

h1{
    color: #008035;
}

</style>