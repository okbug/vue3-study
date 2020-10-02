<template>
<h1>x is {{x}} , y is {{y}}</h1>
</template>

<script lang="ts">
    import { ref, onMounted, onUnmounted} from "vue";
    import useMouseChange from "@/hooks/useMouseChange";
    export default {
        name: "TestMouse",
        setup() {
            const {x,y} = useMouseChange()
            /*
            等同上面
             这些代码逻辑可以通过一个ts/js文件来引入，x, y 是这个函数回值，再在底下return出去 const x = ref(0);
            const y = ref(0);
            const updateMouse = (e: MouseEvent) => {
                x.value = e.pageX;
                y.value = e.pageY;
            }
            onMounted(() => {
                document.addEventListener('click', updateMouse)
            })
            onUnmounted(() => {
                document.removeEventListener('click', updateMouse)
            })*/
            return {
                x,
                y
            }
        }
    }
</script>

<style scoped>

</style>
