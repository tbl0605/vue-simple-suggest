# vue-simple-suggest

A simple autocomplete for Vue 3.

Forked from [@tbl0605/vue-simple-suggest](https://github.com/tbl0605/vue-simple-suggest) which was forked from [@KazanExpress/vue-simple-suggest](https://github.com/KazanExpress/vue-simple-suggest).

## Install

```
npm i @vojtechlanka/vue-simple-suggest
```

## Usage

```html
<template>
  <vue-simple-suggest v-model="valueCurrent" :list="autocompleteItems" :filter-by-query="true" @update:model-select="(item) => selectedCurrent = item"/>
</template>
```

```javascript
<script>
import VueSimpleSuggest from '@vojtechlanka/vue-simple-suggest'
import '@vojtechlanka/vue-simple-suggest/styles.css'

export default {
  components: { VueSimpleSuggest },
  data () {
    return {
      valueCurrent: '',
      selectedCurrent: null,
      autocompleteItems: ['Dog', 'Cat', 'Lizard']
    }
  }
}
</script>
```

All options specified by [original documentation](https://github.com/KazanExpress/vue-simple-suggest) should still work.