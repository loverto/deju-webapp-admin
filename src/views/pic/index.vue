<template>
  <div class="root">
    <div v-for="x in listp" :key="x.index" class="el-table abc " >
      <img :src="'http://th.minio.boyuanziben.cn/boyuanziben/' + x + '_500x500'">
    </div>
  </div>
</template>

<script>
import { list } from '@/utils/file-uploader.js'
export default {
  data() {
    return {
      listp: []
    }
  },
  created() {
    list().then(response => {
      // console.log(response)
      const bb = []
      response.on('data', function(obj) {
        // console.log(obj.name)
        bb.push(obj.name)
      })
      this.listp = bb
      console.log(this.listp)
    })
  }
}
</script>

<style lang="scss" scoped>
  .abc{
    clear: both;
  }
</style>
