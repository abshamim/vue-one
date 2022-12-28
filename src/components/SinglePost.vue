<template>
    <!-- <ul>
        <li>
            <div style="display: inline-block;" v-bind:class="{'fav' : post.fav}">{{ post.title }}</div> | 
            <button @click="deletePost(post)">Delete Post</button>
            <button @click="$emit('fav', post)">Fav Post</button>
        </li>
    </ul> -->
</template>

<script>

export default {
    name: 'SinglePost',
    props: {
        post: {
            type: Object,
            required: true
        }
    },
    methods: {
        deletePost(post){
            this.$emit('deleteUsingEmit', post)
        }
    }
}

</script>

<style scoped>
    .fav{
        color: crimson;
    }
</style>