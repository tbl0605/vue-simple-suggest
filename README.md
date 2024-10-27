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

<script>
import VueSimpleSuggest from '@vojtechlanka/vue-simple-suggest'
// Optional CSS.
import '@vojtechlanka/vue-simple-suggest/style.css'

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

## Breaking changes

When using custom input, listener bindings must be added (provided by the vue-simple-suggest component) to the input element.

For a native html input, bind the slot prop `field`:

```html
<template>
  <vue-simple-suggest v-model="model" ...>
    <template #default="{ field }">
      <input v-bind="field" type="text" ... />
    </template>
  </vue-simple-suggest>
</template>

<script>
import VueSimpleSuggest from '@vojtechlanka/vue-simple-suggest'
// Optional CSS.
import '@vojtechlanka/vue-simple-suggest/style.css'
</script>
```

For a custom input component, bind the slot prop `componentField`:

```html
<template>
  <vue-simple-suggest v-model="model" ...>
    <template #default="{ componentField }">
      <my-custom-input v-bind="componentField" ... />
    </template>
  </vue-simple-suggest>
</template>

<script>
import VueSimpleSuggest from '@vojtechlanka/vue-simple-suggest'
// Optional CSS.
import '@vojtechlanka/vue-simple-suggest/style.css'
</script>
```

Custom asynchronous input components are now also supported, using a [Suspense](https://vuejs.org/guide/built-ins/suspense) component internally.
If set, the `fallback` slot can be used to display content until the `default` slot is resolved:

```html
<template>
  <vue-simple-suggest v-model="model" ...>
    <template #default="{ componentField }">
      <my-custom-async-input v-bind="componentField" ... />
    </template>
    <template #fallback>
      Loading...
    </template>
  </vue-simple-suggest>
</template>

<script>
import VueSimpleSuggest from '@vojtechlanka/vue-simple-suggest'
// Optional CSS.
import '@vojtechlanka/vue-simple-suggest/style.css'
import { defineAsyncComponent } from 'vue'
const MyCustomAsyncInput = defineAsyncComponent(() =>
  import('./MyCustomAsyncInput.vue')
)
</script>
```
## Upgrade from `2.*.*` to `3.*.*`

Only breaking change is the removal of the automatic import of the styles. Now you will have to include `@vojtechlanka/vue-simple-suggest/style.css` just like in the original repository to include the default styles.
