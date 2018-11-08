<template>
  <div>
    <div>
      <input v-validate="'required|myEmail'" name="email" type="text">
    </div>
    <div>
      <span>{{ errors.first('email') }}</span>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import VeeValidate, { Validator } from 'vee-validate';
import zh_TW from 'vee-validate/dist/locale/zh_TW';

/** Custom Validator */
const getMessage = field => `${field} 格式不正確`;

const validate = value => {
  const regex = /^\w+\.*\w+@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z]+$/;
  return regex.test(value);
};

const myValidator = {
  getMessage,
  validate,
};

Vue.use(VeeValidate);
Validator.localize('zh_TW', zh_TW);

/** Custom Rule */
Validator.extend('myEmail', myValidator);

export default {
  name: 'demo',
};
</script>
