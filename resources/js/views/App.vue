<template>
    <div>
        <!-- <h1>Work In Progress</h1> -->
        <WorkInProgress />
        <PostsList :posts="posts" :isLoading="isLoading" />
    </div>
</template>

<script>

import WorkInProgress from '../components/WorkInProgress.vue'
import PostsList from '../components/posts/PostsList.vue'

    export default {
        name: 'App',
        components: {
            WorkInProgress,
            PostsList
        },
        data(){
            return{
                posts: [],
                isLoading: false,

                
            }
        },
        mounted(){
            this.getPosts();
        },
        methods: {
            getPosts(page = 1){
                this.isLoading = true
                axios.get('http://127.0.0.1:8000/api/posts?page=' + page)
                    .then(res =>{
                        console.log(res.data);
                        this.posts = res.data.data;
                    }).catch(err => {
                        console.log(err)
                    }).then(() => {
                        this.isLoading = false
                    })
            }
        }
    }

</script>