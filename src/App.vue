<template>
  <div id="app">
    <FormComponent msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import FormComponent from './components/FormComponent.vue'

export default {
  name: 'App',
  components: {
    FormComponent
  }
}
</script>

<style lang="sass">


*
  margin: 0
  padding: 0
  box-sizing: border-box

body
  display: grid
  align-items: center
  justify-items: center

</style>
