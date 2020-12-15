<template>
    <teleport to="#model" v-if="isOpen">
        <div id="center">
            This is My Content
            <button @click="CloseMe">Close</button>
        </div>
    </teleport>
</template>

<script lang="ts">
    import {defineComponent} from 'vue'

    export default defineComponent({
        name: 'Model',
        props: {
            isOpen: Boolean
        },
        emits: {
            'emit-name': null
        },
        setup(props, context) {

            const CloseMe = () => {
                context.emit('emit-name')
            }

            return {
                CloseMe
            }
        }
    })
</script>

<style>
    #center {
        border: 2px solid black;
        position: absolute;
        width: 120px;
        height: 120px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
</style>
