<template>
    <input type="text" v-model="someText" @keyup.enter="submit">
    {{someText}}
</template>

<script lang="ts">
    import { defineComponent } from "vue";
    import {ref,reactive} from 'vue';

    export default defineComponent({
        name: "MyTodo",
        setup() {
            const someText = ref('')
            const list = reactive([])
            const submit = () => {
                console.log(someText.value)
            }
            return {
                someText,
                submit,
                list
            }
        }
    })
</script>

<style scoped>

</style>
