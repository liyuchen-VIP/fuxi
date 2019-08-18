<template>
  <div class="my-publish">
    <el-card>
      <!-- header -->
      <template slot="header">
        <my-bread>发布文章</my-bread>
      </template>
      <el-form :model="articlesForm" label-width="80px">
        <el-form-item label="标题：">
          <el-input v-model="articlesForm.title" style="width:350px"></el-input>
        </el-form-item>
        <el-form-item label="内容：">
          <quill-editor v-model="articlesForm.content" :options="editorOption"></quill-editor>
        </el-form-item>
        <el-form-item label="封面：">
          <el-radio-group v-model="articlesForm.cover">
            <el-radio :label="1">单图</el-radio>
            <el-radio :label="3">三图</el-radio>
            <el-radio :label="0">无图</el-radio>
            <el-radio :label="-1">自动</el-radio>
          </el-radio-group>
          <el-upload
            action="https://jsonplaceholder.typicode.com/posts/"
            list-type="picture-card"
            :on-preview="handlePictureCardPreview"
            :on-remove="handleRemove"
          >
            <i class="el-icon-plus"></i>
          </el-upload>
          <el-dialog :visible.sync="dialogVisible">
            <img width="100%" :src="dialogImageUrl" alt />
          </el-dialog>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.snow.css'
import 'quill/dist/quill.bubble.css'
import { quillEditor } from 'vue-quill-editor'
export default {
  components: { quillEditor },
  data () {
    return {
      articlesForm: {
        title: '',
        content: '',
        cover: 1
      },
      cover: {
        type: '',
        images: ''
      },
      editorOption: {
        placeholder: '',
        modules: {
          toolbar: [
            ['bold', 'italic', 'underline', 'strike'],
            ['blockquote', 'code-block'],
            [{ header: 1 }, { header: 2 }],
            [{ list: 'ordered' }, { list: 'bullet' }],
            [{ indent: '-1' }, { indent: '+1' }]
          ]
        }
      }
    }
  }
}
</script>
<style scoped lang="less">
.ql-container /deep/ .ql-snow {
  height: 300px;
}
</style>
