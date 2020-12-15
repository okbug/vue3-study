<template>
    <div class="testadd">
<!--        这里是可以不用根DIV的-->
        <h1>Count is :{{count}}</h1>
        <h2>Double is {{double}}</h2>
        <button @click="increase">Click To Add Count</button>
        <button @click="clearCount">Click To Clear Count</button>
    </div>
</template>

<script lang="ts">
    import { ref, computed, reactive, toRefs } from 'vue'
    interface DataProps {
        count: number;
        increase: () => void;
        double: number;
        clearCount: () => void;
    }
    export default {
        name: "TestAdd",
        setup() {
            /* const count = ref(0)
            const double = computed(() => count.value * 2)
            const increase = () => {
                count.value++
            }
            const clearCount = () => {
                count.value = 0
            }
            return {
                count,
                increase,
                clearCount,
                double
            } */
            const data: DataProps = reactive({
                count: 0,
                increase: ()=> data.count++,
                double: computed(() => data.count * 2),
                clearCount: () => {data.count = 0}
            })
            const refData = toRefs(data) // 让代码变得响应式


            return {
                ...refData
            }
        }
    }
</script>

<style scoped>
    .testadd {
        border: solid 3px red;
        width: 550px;
        height: 200px;
        position: absolute;
        top:50%;
        left:50%;
        text-align: center;
        transform: translate(-50%, -50%);
    }
    button {
        margin: 1rem;
    }
</style>
