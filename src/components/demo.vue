<template>
  <div>
    <div>
      <input v-validate="'required|email'" name="email" type="text">
    </div>
    <div>
      <span>{{ errors.first('email') }}</span>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import VeeValidate from 'vee-validate';

Vue.use(VeeValidate);

export default {
  name: 'demo',
};
</script>

<style scoped>

</style>
