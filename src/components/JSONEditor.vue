
<template>
  <div>
    <vue-jsoneditor height="400" mode="tree" :queryLanguagesIds="queryLanguages" :onRenderMenu="handleRenderMenu"
      v-model:json="jsonData" @error="onError" @focus="onFocus" @blur="onBlur" />
  </div>
</template>

<script setup lang="ts">
import VueJsoneditor from 'vue3-ts-jsoneditor';
import { ref } from 'vue';
import type { QueryLanguageId } from 'vue3-ts-jsoneditor'

const jsonData = ref({
  array: [1, 2, 3],
  boolean: true,
  Null: null,
  number: 123,
  seconds: 0,
  object: { a: 'b', c: 'd' },
  string: 'Hello World',
});

const queryLanguages = ref<QueryLanguageId[]>(['javascript', 'lodash', 'jmespath']);

const onError = () => {
  //
}

const onFocus = () => {
  //
}

const onBlur = () => {
  //
}
const selfFun = () => {
  alert('自定义按钮')
  // 获取编辑器中正在编辑的位置，并打印输出
  // const { path, value } = window.jsonEditor.getCursor();
}
const handleRenderMenu = (items: any[]): any[] => {
  console.log(items)
  const selfButton = {
    type: 'button',
    title: '自定义按钮',
    onClick: selfFun,
  }
  items.splice(items.length - 1, 0, { type: 'separator' })
  items.splice(items.length - 1, 0, selfButton)
  return items;
}


</script>


<style scoped>
.svelte-jsoneditor-vue {
  display: flex;
  flex: 1;
}
</style>
