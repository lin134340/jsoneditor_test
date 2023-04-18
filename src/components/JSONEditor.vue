
<template>
  <div>
    <vue-jsoneditor
    height="400"
    mode="tree"
    :queryLanguagesIds="queryLanguages"
    :onRenderMenu="handleRenderMenu"
    v-model:json="jsonData" 
    @error="onError" 
    @focus="onFocus" 
    @blur="onBlur" 
  />
  </div>
</template>

<script setup lang="ts">
  import VueJsoneditor from 'vue3-ts-jsoneditor';
  import {ref} from 'vue';
  import type {QueryLanguageId} from 'vue3-ts-jsoneditor'

  const jsonData = ref({
    array: [1, 2, 3],
    boolean: true,
    Null: null,
    number: 123,
    seconds: 0,
    object: {a: 'b', c: 'd'},
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
  const handleRenderMenu = (items: any[]): any[] => {
    items.forEach((item) => {
      if (item.type === 'button') {
        item.text = `[]${item.text}`;
      }
    });
    return items;
  }
      

</script>


<style scoped>
.svelte-jsoneditor-vue {
  display: flex;
  flex: 1;
}
</style>
