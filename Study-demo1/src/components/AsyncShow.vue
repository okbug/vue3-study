<template>
    <h1>The Image is Show now</h1>
    <h2>{{result.status}}</h2>
    <img :src="result.message">
</template>

<script lang="ts">
    import axios from 'axios'
    import {defineComponent} from "vue";
    export default defineComponent({
        name: "AsyncShow",
        async setup() {
            const rawData = await axios.get('https://dog.ceo/api/breeds/image/random')
            return {
                result:rawData.data
            }
        }
    })
</script>

<style scoped>

</style>
