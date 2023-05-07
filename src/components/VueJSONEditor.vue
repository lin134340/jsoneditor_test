<template>
  <div ref="container"></div>
</template>
  
<script lang="ts" setup>
import { JSONEditor, RenderValueProps, renderValue } from "vanilla-jsoneditor";
import { onMounted, ref } from "vue";

const content = {
  json: {
    greeting: "Hello World",
    color: "#ff3e00",
    ok: true,
    values: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15],
  },
  text: undefined,
};

// const propNames = [
//     "content",
//     "mode",
//     "mainMenuBar",
//     "navigationBar",
//     "statusBar",
//     "readOnly",
//     "indentation",
//     "tabSize",
//     "escapeControlCharacters",
//     "escapeUnicodeCharacters",
//     "validator",
//     "onError",
//     "onChange",
//     "onChangeMode",
//     "onClassName",
//     "onRenderValue",
//     "onRenderMenu",
//     "queryLanguages",
//     "queryLanguageId",
//     "onChangeQueryLanguage",
//     "onFocus",
//     "onBlur",
// ];

const container = ref();
const editor = ref();

const onChange = (content: any, previousContent: any, changeStatus: any) => {
  console.log("onChange", content, previousContent, changeStatus);
};

const selfFun = () => {
  console.log(editor.value);
  const json = editor.value.get();
  // const selected_node = editor.value.getSelectedNode();
  console.log("selfFun", json);
  // alert('自定义按钮')
  // 获取编辑器中正在编辑的位置，并打印输出
  // const { path, value } = window.jsonEditor.getCursor();
}
const onRenderMenu = (items: any[], context: any): any[] => {
  // console.log(items)
  console.log(context)
  const selfButton = {
    type: 'button',
    title: '自定义按钮',
    onClick: selfFun,
  }
  items.splice(items.length - 1, 0, { type: 'separator' })
  items.splice(items.length - 1, 0, selfButton)
  return items;
}

const onRenderValue = (props: RenderValueProps) => {
  console.log(props.selection);
  return renderValue(props);
};

onMounted(() => {
  editor.value = new JSONEditor({
    target: container.value,
    props: {
      content,
      onChange: onChange,
      onRenderMenu: onRenderMenu,
      onRenderValue: onRenderValue,
    }
  });
});



</script>
  
<style scoped></style>