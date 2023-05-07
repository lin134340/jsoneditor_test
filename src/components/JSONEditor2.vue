<template>
  <div ref="jsonEditor"></div>
</template>

<script lang="ts">
import { ref, onMounted } from 'vue';
import JSONEditor from 'vanilla-jsoneditor';

export default {
  setup() {
    const jsonEditorRef = ref<HTMLElement | null>(null);

    onMounted(() => {
      if (jsonEditorRef.value) {
        const jsonEditor = new JSONEditor(jsonEditorRef.value);
        // 其他配置和使用方法
      }
    });

    return {
      jsonEditorRef,
    };
  },
};
</script>
