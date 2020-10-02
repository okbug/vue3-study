<template>
  <h1>{{msg}}</h1>
  <TestMouse></TestMouse>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TestMouse from "@/components/TestMouse.vue";

export default defineComponent({
  name: 'App',
  data() {
    return {
      msg:'我可以不是一个根节点'
    }
  },
  components: {
    TestMouse
  }
})
</script>

<style scope>
h1 {
  justify-content: center;
}
</style>
