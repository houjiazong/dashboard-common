<template>
  <base-dialog @cancel="cancelDialog">
    <div slot="header">日志查看</div>
    <div class="clearfix pr-2" slot="body">
      <code-mirror v-model="params.data" :options="cmOptions" ref="codeMirrorRef" view-height="300px" :is-scroll="true" />
      <div
        class="float-right"
        v-clipboard:copy="params.data"
        v-clipboard:success="copySuccess"
        v-clipboard:error="copyError">
        <a-icon class="primary-color" type="copy" />
        <a-button type="link" size="small">复制内容</a-button>
      </div>
    </div>
    <div slot="footer">
      <a-button type="primary" @click="cancelDialog">{{ $t('dialog.ok') }}</a-button>
    </div>
  </base-dialog>
</template>

<script>
import DialogMixin from '@/mixins/dialog'
import WindowsMixin from '@/mixins/windows'

export default {
  name: 'EventLogDialog',
  mixins: [DialogMixin, WindowsMixin],
  data () {
    return {
      cmOptions: {
        tabSize: 2,
        indentUnit: 2,
        smartIndent: true,
        lineNumbers: true,
        readOnly: true,
        theme: '3024-day',
        lineWrapping: true,
        mode: 'application/json',
        gutters: ['CodeMirror-lint-markers'],
        lint: true,
      },
    }
  },
  methods: {
    copySuccess (evt) {
      this.$message.success('复制成功')
    },
    copyError () {
      this.$message.error('复制失败')
    },
  },
}
</script>
