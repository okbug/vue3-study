<template>
  <div>
    <div class="todo-container">
      <div class="todo-wrap">
        <div class="todo-header">
          <input type="text" v-model="msg" @keyup.enter="func"/>
        </div>
        <a :href="f" v-if="isShow" download="abc.mp4" target="_blank">点击跳转</a>
        <a href="#" v-if="loading">加载中</a>
      </div>
      <video :src="f" controls="controls" v-if="isShow"></video>
    </div>
    
  </div>
</template>

<script lang="ts">
/**
 * https://v.douyin.com/JyQgFs9
 */
import { defineComponent, Ref, ref } from "vue";
export default defineComponent({
  setup() {
    const msg = ref("");
    const isShow = ref(false)
    const loading = ref(false)
    let v = {
        mp4: {
            location:''
        }
    }
    const f: Ref = ref('')
    const func = () => {
        if(msg.value !== '') {
            loading.value = true
            fetch('http://api.131438.xyz/douyin.php?url=' + msg.value).then(e=>e.json()).then(d=> v = d)
                .then(() => {
                    const c = v.mp4.location
                    const d: string[] = c.split('com/')
                    f.value = 'https://v3-dy-a.ixigua.com/'+d[1]
                    isShow.value = true
                    loading.value = false
                })
        }
    }
    return {
      msg,
      func,
      f,
      isShow,
      loading
    };
  },
});
</script>

<style scoped>
</style>