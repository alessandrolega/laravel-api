<template>
    <div>
        <Loader v-if="isLoading" />
            <ul v-else-if="posts.length">
                <li v-for="elem in posts" :key="elem.id">{{ elem.title }}</li>
            </ul>
            <p v-else>Non ci sono dati nel DB</p>

            <Pagination />
        </div>
</template>


<script>

import Loader from '../Loader.vue'
import Pagination from '../Pagination.vue'


    export default {
        name: 'PostsList',
        components:{
            Loader,
            Pagination
        },
        props: ['posts', 'isLoading']
    }

</script>