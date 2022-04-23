<template>
    <div v-for="thread in threads" :key="thread.id">
        <h2>
            <!-- {{thread.title}} -->
            <div v-for="postId in thread.posts" :key="postId">
                <small>{{userById(postById(postId).userId).name}}</small>
                <p>{{postById(postId).text}}</p>
            </div>
        </h2>
    </div>
</template>

<script>
import data from '@/data/data.json';

export default {
    data() {
        return {
            threads: data.threads,
            posts: data.posts,
            users: data.users
        }
    },
    methods: {
        postById(postId) {
            return this.posts.find(p => p.id === postId)
        },
        userById(userId) {
            return this.users.find(u => u.id === userId)
        }
    }
}

</script>

<style scoped>
    p {
        font-weight: 100;
    }
</style>
