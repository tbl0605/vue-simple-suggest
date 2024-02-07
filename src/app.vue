<template>
  <div class="mainWrapper">
    <div>
      <strong>Simple example</strong>
      <div>Current value: {{ value.simple }}</div>
      <div>Current selected: {{ selected.simple }}</div>
      <vue-simple-suggest v-model="value.simple" :list="autocompleteItems.simple" :filter-by-query="true" @update:model-select="(item) => selected.simple = item" />
    </div>
    <hr>
    <div>
      <strong>Object suggestion example</strong>
      <div>Current value: {{ value.object }}</div>
      <div>Current selected: {{ selected.object }}</div>
      <vue-simple-suggest
        v-model="value.object" :list="autocompleteItems.object" display-attribute="name" value-attribute="id"
        :filter-by-query="true" @update:model-select="(item) => selected.object = item"
      />
    </div>
  </div>
</template>

<script>
import VueSimpleSuggest from '../dist/vue-simple-suggest'
// import VueSimpleSuggest from './vue-simple-suggest.vue'

export default {
  name: 'App',
  components: { VueSimpleSuggest },
  data () {
    return {
      value: {
        simple: '',
        object: null
      },
      selected: {
        simple: '',
        object: null
      },
      autocompleteItems: {
        simple: ['Dog', 'Cat', 'Lizard'],
        object: [{ name: 'Dog', id: 1 }, { name: 'Cat', id: 2 }, { name: 'Lizard', id: 3 }]
      }
    }
  }
}
</script>

<style>
.mainWrapper {
  width: 70vw;
  margin-left: auto;
  margin-right: auto;
}
</style>
