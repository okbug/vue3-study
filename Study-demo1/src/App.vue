<template>
    <h1>{{msg}}</h1>
    <button @click="handleClick">Click</button>
    <Model :isOpen="ModelIsOpen" @emit-name="onModalClose"></Model>
    <Suspense>
        <template #default>
          <AsyncShow></AsyncShow>
        </template>
        <template #fallback>
            <h1>Loading...</h1>
        </template>
    </Suspense>
</template>

<script>
    import {defineComponent, ref, onMounted} from 'vue';
    import Model from "@/components/Model.vue";
    import AsyncShow from "@/components/AsyncShow.vue";

    export default defineComponent({
        name: 'App',
        data() {
            return {
                msg: 'For Nothing'
            }
        },
        components: {
            Model,
            AsyncShow
        },
        setup() {
            const ModelIsOpen = ref(false)
            const handleClick = () => {
                ModelIsOpen.value = true
            }
            const onModalClose = () => {
                ModelIsOpen.value = false
            }
            return {
                ModelIsOpen,
                handleClick,
                onModalClose
            }
        }
    })
</script>

<style scope>
    h1 {
        justify-content: center;
    }
</style>
