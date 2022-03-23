<template>
  <div class="app">
    <p> {{name}} </p>
    <button @click="changeName('Zelda')">change name</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components: {},
  data() {
    return {
      name: 'Link'
    }
  },
  methods: {
    changeName(name: string) {
      this.name = name
    }
  }
});
</script>

<style>

</style>
