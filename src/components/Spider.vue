<template>
    <div v-for="item in newsList">
        <p>{{ item.title }}</p> 
    </div>
</template>
  
<script>
import axios from 'axios'
export default {
    data() {
        return {
            newsList: []
        }
    },
}
</script>