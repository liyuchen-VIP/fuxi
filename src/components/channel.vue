<template>
  <el-form-item label="频道：">
    <el-select v-model="screenForm.channel_id" size="small">
      <!--
                  指定 key 作为唯一标识
                  label 看到的文字
                  value 文字的值
      -->
      <el-option v-for=" item in channelOptions" :key="item.id" :label="item.name" :value="item.id"></el-option>
    </el-select>
  </el-form-item>
</template>

<script>
export default {
  name: 'my-channel'
}
</script>
<style scoped lang="less">
</style>
