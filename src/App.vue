<template>
  <div id="app">
    <Form />
    Hello world
  </div>
</template>

<script>
import { required, minLength, between } from 'vuelidate/lib/validators'

import Form from './components/Form'

export default {
  name: 'App',
  components: {
    Form
  },
  data() {
    return {

    }
  },
  validations: {
    name: {
      required,
      minLength: minLength(4)
    },
    age: {
      between: between(20, 30)
    }
  }
}
</script>

<style>

</style>
