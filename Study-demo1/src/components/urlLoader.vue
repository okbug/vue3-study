<template>
    <h1 v-if="loading">Now is Loading</h1>
    <img v-if="loaded" :src="result.message">
</template>

<script>
    import useURLLoader from "../hooks/useURLLoader";

    export default {
        name: "urlLoader",
        setup() {
            const {result, loaded, loading, error} = useURLLoader('https://dog.ceo/api/breeds/image/random')
            return {
                result,
                loaded,
                loading,
                error
            }
        }
    }
</script>

<style scoped>

</style>
